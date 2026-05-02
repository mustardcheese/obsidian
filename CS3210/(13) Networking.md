## What does networking look like to the OS?

At the lowest level, a NIC talks **directly** to another NIC.

- **Point-to-point** communication — two wires/cards talking to each other.
- This is _all_ the hardware really gives us.

### Orthogonality and Composability

How do we go from raw NIC ↔ NIC links to a worldwide _anywhere-to-anywhere_ network? The building blocks must satisfy:

- **Orthogonality** — a small set of primitive constructs can be combined in a small number of ways to build everything.
- **Composability** — components can be selected and assembled in many combinations to satisfy specific requirements.

---

# Networking Abstraction

The raw point-to-point view isn't usable for apps. We abstract the network as a **cloud of routers** between two NICs — the app just sees "send data here, it arrives there."

![[Pasted image 20260317141755.png|500]]

## Internet Abstraction (what the OS _promises_ applications)

- **Naming** — URLs / domain names (e.g. `gatech.edu`)
- **Point-to-point** — app-to-app (or host-to-host), abstracting all routers in between
- **Multiplexing** — 1 NIC, many ports; many connections per port
- **Streaming** — semantically continuous flow of data, not packets
- **Reliability** — surviving failures (non-trivial)

## Hardware Abstraction (what the NIC _actually_ gives)

- A single network interface
- **Unreliable** transport — can reorder packets, drop data, duplicate
- Communicates via **MAC address**
- **No security**

> _Bare-bones, frame-based, unreliable point-to-point comm system._

![[Pasted image 20260317143029.png|500]] 
_Data Link Layer — MAC address layout (6 octets: 3-octet OUI + 3-octet NIC-specific ID)._

## OS Abstractions (closing the gap)

- **Reliable** transport
- **Naming** — hostname communication
- **Multiplexing** — many ports per NIC
- **Fine-grain multiplexing** — many connections per port
- **Protection** — secure transport layers (kind of)

The **gap** between hardware and OS abstractions is filled by the **networking stack**.

---

# How do we build these abstractions?

Networking is built in **layers** (7 in the OSI standard, but we focus on 4 + app):

|Layer|Examples|
|---|---|
|Application|HTTP, FTP|
|(L4) Transport|TCP, UDP|
|(L3) Network|IP|
|(L2) Data Link|IEEE 802.3 (Ethernet), 802.11 (WiFi)|
|(L1) Physical|Ethernet, fiber, radio|

Mnemonic: _All People Seem To Need Data Processed._ Application / Presentation / Session are usually lumped as "application layer."

> "**LX-capable**" means a device can process headers at layer X. A router is **L3-capable** because it performs IP routing.

---

# How the Layers Work

Each layer adds its own **header** (loosely: protocol == header). Like an onion — peel one header per layer as you move up.

- **NICs** process Physical / MAC (L1, L2)
- **OSes** process Network / Transport (L3, L4)

![[Pasted image 20260317144310.png|550]]

### Header / chunk names (don't confuse these on the exam)

|Layer|Unit|Header adds|
|---|---|---|
|L2 Data Link|**Frame**|Sender + receiver MAC, FCS|
|L3 Network|**Packet**|Sender + receiver IP|
|L4 Transport|**Segment**|TCP/UDP port, protocol info|

### End-to-end stack propagation

- **Link layer** — communicates over a _single hop_ (e.g. one Ethernet cable)
- **Internet layer** — manages _multiple hops_ across links (host addressing + routing)
- **Transport layer** — _host-to-host_ reliability
- **Application layer** — _process-to-process_ communication

![[Pasted image 20260317144514.png|550]]

---

## Internet Layer (L3)

Manages multiple hops across links via:

- **Host addressing** (IP)
- **Routing** — picking a path through the router cloud

![[Pasted image 20260317144729.png]]

Routing is essentially a large-scale distributed system problem (covered in depth in a Networking class).

---

## Transport Layer (L4) — _of particular interest to the OS_

### TCP goals

- **Stream interface** — looks like a stream of arbitrary writes, not packets
- **Reliability** — no losses, no duplicates, no reordering visible to the app
- **Point-to-point** — direct host-to-host

### Building a stream from packets

We're given ~1500-byte packets. To fake a byte stream:

- Multiple writes per packet, or one write split across packets
- But packets can be **reordered** or **dropped** — how do we cope?

### OS stream support — Detection + Correction

Every failure mode needs both:

- **Detection** — notice the failure happened
- **Correction** — fix it

|Failure|Mechanism|
|---|---|
|Out-of-order packets|**Sequence numbers** → reorder at receiver|
|Dropped packets|**Retransmission** + **timeout**|
|Duplicates|Discard by sequence number|
|Bit errors|Checksum|

### TCP vs UDP tradeoffs

**TCP — reliable:** byte-stream, no errors, no duplicates, no drops
**UDP — minimal:** only checksum (no errors), no retransmit / ordering / streams.

Why use UDP?

- **Latency-sensitive** (video calls, games) — a retransmitted frame from 200 ms ago is useless
- **Custom reliability at the app layer** (e.g. QUIC)
- **Broadcast / multicast** — TCP is point-to-point only

---

# TCP/IP in Linux

The **Host–Network Gap** is bridged by the kernel via:

- **Socket Interface** — BSD sockets (generic) on top of INET sockets (IP-specific). Apps invoke via syscalls (`socket()`, `send()`, `recv()`).
- **Transport layer modules** — TCP, UDP
- **Network layer module** — IP
- **Datalink drivers** — Ethernet, PPP, etc.
- **Netfilter framework** — hooks (PREROUTING, POSTROUTING, FORWARD, LOCAL_IN, LOCAL_OUT) used by firewalls / `iptables` to inspect, modify, or drop packets.

## Packet RX/TX in Linux

**Receive (RX) path** — wire → app:

1. Packet arrives at NIC; **DMA** writes it into a kernel **ring buffer**
2. NIC raises an **interrupt** → handler schedules a **softirq** (deferred work)
3. Softirq runs `ip_rcv()` → `tcp_v4_rcv()` → socket backlog
4. Data lands in the **TCP receive buffer** (`tcp_rmem`)
5. App calls `read()`


**Transmit (TX) path** — app → wire:

1. App calls `write()` → **TCP send buffer** (`tcp_wmem`)
2. TCP processes (`tcp_transmit_skb`) → IP layer (`ip_queue_xmit`)
3. Packet enters **qdisc** (queue discipline / scheduling) at `txqueuelen`
4. Driver `hard_start_xmit` → DMA pushes to NIC → NIC sends
5. Completion queue + softirq frees the descriptor

Key takeaways:

- **DMA** moves data to/from kernel memory without CPU involvement
- Interrupt handlers are **fast**; real work runs in deferred **softirqs**

---

# Extended Berkeley Packet Filter (eBPF)

**Problem:** custom kernel modules are painful + risky (one bug = panic), but we want high performance and customization.

**Solution:** sandboxed programs that run _inside_ the kernel.

1. User writes a program (e.g., packet tracer/filter)
2. Compile to **eBPF bytecode**
3. **In-kernel verifier** statically checks safety (no infinite loops, no OOB memory)
4. **JIT-compile** to native instructions
5. **Attach** to specific kernel events (syscalls, network hooks, function entry/exit)

### Example: block all IPv6

- **Old way:** kernel allocates an `sk_buff` for every packet, walks it up the stack, checks IP version, drops it. Slow — exploited by DDoS.
- **eBPF way:** attach an XDP (eXpress Data Path) program at the **NIC driver level**. Inspect Ethernet header on arrival; if IPv6, return `XDP_DROP` _before_ any allocation.

```c
SEC("xdp")
int filter_ipv6(struct xdp_md *ctx) {
    void *data = (void *)(long)ctx->data;
    struct ethhdr *eth = data;
    // bounds checks (verifier requires these)
    if (is_ipv6(eth)) return XDP_DROP;
    return XDP_PASS;
}
```

This is the foundation of modern DDoS protection (Cilium, Katran, etc.).