# Resume Project Ideas

**Key:** 🟢 Weekend (~1-2 days) | 🟡 1-2 weeks | 🔴 3+ weeks

---

## 1. Computer Architecture

- 🟢 **Microarchitecture discovery tool (C/C++):** Microbenchmarks that measure cache sizes, latencies, TLB reach, memory bandwidth, and SIMD throughput. Validate against published specs. _Metric: measured values within X% of spec._
- 🟡 **Trace-driven cache + prefetcher simulator (C++):** Multi-level hierarchy with LRU vs. SRRIP replacement and a stride prefetcher, run on real traces from Pin/Valgrind. _Metric: MPKI reduction and estimated IPC gain per policy._
- 🟡 **Branch predictor shootout:** Implement bimodal, gshare, and TAGE-lite, and evaluate on real branch traces. _Metric: misprediction rate per predictor and per workload._
- 🔴 **Pipelined RISC-V core in SystemVerilog:** 5-stage pipeline with forwarding and hazard detection, plus a self-checking testbench against a reference model. _Metric: passes riscv-tests, CPI on benchmarks._
- 🔴 **Out-of-order core simulator:** ROB, reservation stations, and register renaming in C++, validated on small kernels. _Metric: IPC vs. in-order baseline._

---

## 2. HPC at Scale

- 🟢 **Roofline profiling of your existing kernels:** Measure achieved FLOPs and bandwidth for matmul, stencil, and SpMV against machine peak. _Metric: % of peak for each kernel._
- 🟡 **Hybrid MPI + OpenMP 3D stencil (Jacobi/heat equation):** Domain decomposition with halo exchange, overlapping communication and compute. _Metric: strong/weak scaling efficiency at N ranks._
- 🟡 **Distributed FFT or transpose-based solver:** Pencil or slab decomposition with MPI_Alltoall, compared against FFTW-MPI. _Metric: scaling curve and % of library performance._
- 🔴 **Mini-app port with a performance study (e.g., MFEM-style or LULESH-like):** Profile, find the bottleneck, optimize, and document the speedups. Ties directly to your LLNL work. _Metric: end-to-end speedup and scaling to N nodes._
- 🔴 **Communication-avoiding or pipelined Krylov solver (CG/GMRES):** Reduce global reductions and measure the effect at scale. _Metric: time-to-solution vs. baseline CG at high rank counts._

---

## 3. Concurrency / Caching / Cache Coherence

- 🟢 **False sharing and memory-ordering lab:** Benchmarks demonstrating false sharing, padding fixes, and acquire/release vs. seq_cst costs, with `perf c2c` evidence. _Metric: X× speedup from layout fixes._
- 🟡 **MESI/MOESI coherence protocol simulator:** Multi-core, directory- or snoop-based, with a trace generator for sharing patterns. _Metric: invalidation and traffic counts across workloads._
- 🟡 **Lock-free queue and stack suite (C++):** MPMC ring buffer, Michael-Scott queue, and Treiber stack, compared against mutex baselines. _Metric: throughput at N threads, tested with TSan._
- 🟡 **Work-stealing task scheduler (C++ or Rust):** Chase-Lev deques with careful memory ordering, benchmarked against OpenMP tasks/TBB on fib, quicksort, and BFS. _Metric: speedup and steal-rate analysis._
- 🔴 **Concurrent hash map or cache (lock-free or fine-grained):** Compare striped locks, lock-free open addressing, and RCU-style reads under skewed workloads. _Metric: ops/sec scaling to N cores vs. `std::unordered_map` + mutex._

---

## 4. Distributed Systems

- 🟢 **Ring allreduce from scratch:** Implement over MPI point-to-point or sockets, compare against MPI_Allreduce/NCCL, and fit an α-β latency/bandwidth model. _Metric: % of library bandwidth, model fit error._
- 🟡 **Distributed key-value store with consistent hashing and replication:** Gossip-based membership, quorum reads/writes, and failure injection. _Metric: throughput and latency under node failures._
- 🟡 **MapReduce-style framework:** Coordinator plus workers, fault tolerance via task re-execution, and word count / PageRank as workloads. _Metric: scaling with workers, recovery time after a kill._
- 🔴 **Raft consensus implementation:** Leader election, log replication, and snapshotting, tested with a fault-injection harness (Jepsen-style). _Metric: linearizability checks passed, election time under partitions._
- 🔴 **Sharded, replicated KV store on top of Raft:** Multi-group Raft with shard migration, following the MIT 6.5840 design. _Metric: throughput across shards, correctness under partitions._

---

## 5. GPU Acceleration

- 🟢 **GPU primitives ladder (reduction, scan, histogram):** Optimize each step by step (coalescing, shared memory, warp shuffles), documenting the gain at each stage. _Metric: % of peak memory bandwidth, speedup per optimization._
- 🟡 **CUDA GEMM optimization ladder:** Naive → tiled → register blocking → vectorized loads → double buffering (→ tensor cores), compared against cuBLAS. _Metric: % of cuBLAS GFLOPs._ (This is your resume replacement.)
- 🟡 **SpMV format shootout (CSR, ELL, SELL-C-σ) on GPU:** Profile with Nsight and explain each format's behavior via roofline analysis. _Metric: GFLOPs and bandwidth utilization per format and matrix type._
- 🟡 **GPU stencil / Navier-Stokes kernel:** Shared-memory tiling and temporal blocking on a 2D/3D solver. _Metric: speedup over the CPU version and % of bandwidth peak._
- 🔴 **Fused attention kernel (FlashAttention-style):** Tiled online softmax fused in one kernel, compared against a naive PyTorch implementation. _Metric: speedup and memory reduction vs. naive attention._
- 🔴 **Multi-GPU scaling study (NCCL/CUDA-aware MPI):** Halo exchange or data-parallel training with overlapped communication. _Metric: multi-GPU scaling efficiency._
