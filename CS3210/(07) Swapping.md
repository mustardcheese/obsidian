## Memory Backing

- Physical memory is **NOT** limited by RAM
- Virtual mappings do **NOT** have to be backed by RAM

Two techniques exploit this:

_Swapping_ — Saving memory to disk when we run out of RAM; "swap" some memory to disk. The backing store is a dedicated swap partition/file.

_Memory Mapping_ — Mapping file information into virtual addresses, and writing it back to the file. The backing store is the file itself.

---

## Page Eviction: Which Pages to Swap Out?

### Belady's Optimal Algorithm

- Evict the page that will be accessed **furthest in the future**
- Provably optimal — minimizes page faults
- **Impossible in practice** — requires knowledge of the future
- Useful only as a theoretical benchmark to compare other algorithms against

### Least Recently Used (LRU)

Since we can't know the future, we approximate: the page used **longest ago** is likely not needed soon (temporal locality).

**Why LRU is too expensive to implement exactly:**

- Requires recording a **timestamp on every single memory access** (every load AND store)
- Even with an O(1) data structure update, the per-access overhead is unacceptable
- **Unnecessary overhead even with infinite memory** — you'd pay the cost even if you never need to evict
- Worst overhead: trapping (page fault) on **every** access just to let the OS record the timestamp
- Complexity of maintaining sorted timestamps: O(n) → O(log n) → O(1), but update must happen on **each memory access** regardless

**LRU is impractical for pages** (though it works fine for smaller structures like CPU caches where hardware tracks access order directly).

---

## Clock (Second Chance) Algorithm

An efficient **approximation of LRU** using a single access bit per page instead of full timestamps.

### Data Structures

- Pages arranged in a **circular buffer** (circular list)
- Each page has an **access bit (a)**: hardware sets it to 1 on any read or write
- A **clock hand** (pointer) that advances around the circle
- A monotonically increasing **clock counter (CAC)** tracks the hand's position
![[Pasted image 20260310162759.png]]
### Algorithm: On Eviction

The clock hand sweeps forward through the circular buffer:

1. **If a == 1** (page was accessed): clear the bit to 0 ("second chance"), advance the hand
2. **If a == 0** (page was NOT accessed since last sweep): **evict this page**

The hand keeps advancing and clearing bits until it finds a page with a == 0.
![[Pasted image 20260310162824.png|600]]
![[Pasted image 20260310162845.png|600]]

### Access Bit Transitions

|Transition|What causes it|Meaning|
|---|---|---|
|**0 → 1**|A process reads/writes the page → **page fault trap**|The OS is notified of the access and sets a=1. This is the ONLY time we need to trap.|
|**1 → 0**|Clock hand passes over this page during eviction sweep|"Second chance" used up — if still a=0 next time, it gets evicted|
|**1 → 1**|Page was accessed again between two sweeps of the clock hand|Page is actively in use — safe for now|
|**0 → 0**|Page not accessed, clock hand hasn't passed it yet|Sitting idle, prime eviction candidate|

![[Pasted image 20260310162942.png]]

**Key efficiency insight:** We only trap when transitioning 0 → 1 (the first access after a clear), NOT on every single read/write. This is what makes the clock algorithm so much cheaper than true LRU.

### How the Trap Works

When the clock hand clears a page's access bit (a = 0), the OS also clears **PTE_P** (present bit) in the page table entry. This means:

- When a == 0, PTE_P == 0
- Next access by any process → hardware sees PTE_P = 0 → **page fault**
- Page fault handler sets a = 1, restores PTE_P = 1, resumes execution
- All subsequent accesses hit normally with no trap (until the clock hand clears it again)

### Worst-Case Complexity

If **all** pages have a == 1 (every page was recently accessed):

1. **First full sweep:** clock hand visits all N pages, clearing each from a=1 to a=0. No eviction yet.
2. **Second sweep:** clock hand comes back around, now all pages have a=0. Evicts the first one it reaches.

**Worst case: 2N page inspections** to find a single page to evict (N to clear + N to find a=0 on second pass).

In practice this is rare — usually some pages have a=0 and the hand finds a victim quickly.

---

## xv6 Specifics

- In xv6, page fault handling happens via **vector 14** in the interrupt descriptor table
- The page fault handler in `trap.c` is where Lab 2 swapping code lives
- PTE flags like `PTE_P` (present), `PTE_A` (accessed) are defined in the page table entry structure
- xv6 runs on x86 which provides hardware support for the accessed bit (`PTE_A`) — the hardware sets this bit automatically on page access, which simplifies the clock algorithm implementation