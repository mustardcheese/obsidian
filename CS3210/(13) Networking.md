What does networking look like to the OS?
- The standard network interface card communicates directly with other network interface card (NIC)
- Point to point communication -- two wires talking to each other by direct connection at the lowest level

### Orthogonality and Composability
How do we go from NIC <-> NIC communication to the world wide web?
- Anywhere to anywhere communication

It is fundamental we follow two properties:
- **Orthogonality:** A relatively small set of primitive constructs can be combined in a relatively small number of ways to build everything
- **Compsability:** A system design principle that allows for highly composable components to be selected and combined to make a build anything

# Networking Abstraction
What does networking look like to the OS?
- Point to point NIC to NIC communication

This point to point abstraction isn't really usable for OS users or application developers
- We need something simpler and easier
- **Communication is based on your NIC sending info sent to other routers which can eventually lead to NIC**
- It abstracts away the NIC to NIC connectivity without dealing with everything in between
![[Pasted image 20260317141755.png|500]]
- So how do we choice how we set up this 'cloud' of router to router communication?

## Internet Abstraction
How does this "internet" abstraction work for the user
- url/domain name (addressng/naming)
- Point to Point communication (app to app communication, higher level than just point to point)
- Multiplexing (1 NIC, many connections)
- Streaming (semantically relevant data, constant streams/flow of data)
- Reliability (surviving failures)

## Hardware Abstraction
- Provide a single networking interface
- Unreliable transport
	- Can reorder packets
	- Can drop data
	- as
- Communicate to MAC address
- No security

*barebones frame based unreliable p2p system*

![[Pasted image 20260317143029.png|500]]
Data Link Layer -- MAC address layout

## OS Abstractions
- *Reliable* transport
- Naming: host name communication
- Multiplexing: multiple ports per network card
- Fine grain multiplexing: multiple types of connections per port
- Protection: Secure transport layers

# How do we build abstractions?
Networking is built in layers (7 Standard Layers)
- Physical (Ethernet/fiber)
- Data Link
- Network (IP)
- Transport (UDP,TCP)
- Higher Levels (ignore for now)

*All People Seem To Need Data Processed*
- Application
- Presentation
- Session
--------------- ^^ typically just referred to as application layer
- (L4) Transport
- (L3) Networking
- (L2) Data Link (aka Link)
- (L1) Physical

When something is LX capable, it means it can handle the headers of that 'L' level
- A router is an L3 capable device because it can perform routing

# Networking Layers
Like an onion, each layer we move through means another layer we have to unwrap
- NICs process PHY/MAC
- OSes process Network & Transport
![[Pasted image 20260317144310.png|550]]


![[Pasted image 20260317144514.png|550]]
Lots of interaction and routing in-between

## Internet (L3)
Internet manages multiple hops across links
- Host addressing (IP)
- Routing

How do we construct the *mechanism* for IP address
How do we route?
![[Pasted image 20260317144729.png]]
- Essentially just take an optimize weighted route of a DAG

## Transport (L4)
Layer of interest to the OS

TCP Provides:
- Streaming interface (data comes in streams instead of packets)
	- How have packets, how can we make it look like a stream of arbitrary writes
- Multiple packets per write, or put multiple writes in a packet
- What if packets are reordered or dropped? How do we handle it?

**fill in notes i missed past this i really need to sleep so bad**