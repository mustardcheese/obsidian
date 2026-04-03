take notes

Communicators are abstractions that help group processors together
- Constructors are collective operations

# Topologies
Virtual topologies are digital ones that are abstracted from physical topology
- MPI provides a mechanism to describe logical organization
- MPI implementation may use virtual topologies to assign MPI processes to physical processors
![[Pasted image 20260316094433.png|500]]
Virtual and Physical topologies can be modeled as graphs and can be fed into MPI

## Graph Topologies
![[Pasted image 20260316094531.png|350]]
"[Fat Tree](https://en.wikipedia.org/wiki/Fat_tree)" topology -- go both ways and more arrows represent higher bandwidth

Graphs can be represented as an adjacency matrix
- For n vectors, $n\times n$ size vector
- In the real world though, we don't want to store zeroes -- it's very wasteful
![[Pasted image 20260316094801.png|500]]
Adjacency Lists are the straightforward representation, but they aren't efficient because of caches
- What if we "color" the adjacency list and turn that into an array?
![[Pasted image 20260316094935.png|500]]
**CSR (Compressed Sparse Row) format**
- Very important, very commonly used
- *Optimized less cache misses*
- For a weighted graph also keep a list for the weights
![[Pasted image 20260316095123.png|300]]
![[Pasted image 20260316095136.png|150]]

## How does MPI use these topologies?

``` C
int MPI_Graph_Create(MPI_Comm comm, int nnodes, int* index, int* edges, int reorder, MPI_Comm* newcomm);
```
- No performance guarantees for parallel edges
- Edge direction does not imply a direction of the communication
![[Pasted image 20260316095428.png|350]]
- Find a way to constructed the index list and edge list

**Vertices** represent an MPI processes
**Edges** indicate *some* connection
Edge **weights** provide additional info, such as volume

```C
int MPI_Dist_graph_create_adjacent(MPI_Comm comm_old, int indegree, const int sources[], const int sourceweights[], int outdegree, const int destinations[], const int destweights[], MPI_Info info, int reorder, MPI_Comm *comm_dist_graph)
```
- Able to specify graph topology without any communication
![[Pasted image 20260316100259.png|500]]
- Much more simplified
- Each process knows input/output without knowledge of the complete topology

```C
int MPI_Dist_graph_create(MPI_Comm comm_old, int n, const int sources[],
const int degrees[], const int destinations[],const int weights[],
MPI_Info info, int reorder, MPI_Comm *comm_dist_graph)
```
- Establishes the communication for sender and receiver

## Cartesian Topology
![[Pasted image 20260316101447.png|400]]
i dont fucking know bruh