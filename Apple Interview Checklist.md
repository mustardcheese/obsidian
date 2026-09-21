
## Priority Order

- [ ] 1. Resume — know every bullet cold
- [ ] 2. GPU arch + rendering pipeline
- [ ] 3. Comp arch fundamentals
- [ ] 4. DV engineer mindset (spec → model → verify)
- [ ] 5. Verification fundamentals
- [x] 6. Verilog/SV basics
- [ ] 7. UVM vocab
- [ ] 8. Coding warm-up

## 1. Resume

- [ ] MFEM/Crystal Router (LLNL) — PIC MPI algo, log₂(P) bisection, vs. gs/halo exchange
- [ ] SpGEMM (C++/MPI)
- [ ] CS2200 TA — pipelining/hazards/scheduling/memory
- [x] CRNCH Verilog — comp arch understanding, not RTL career
- [ ] For each: what it does · why that approach · how correctness was verified

## 2. GPU Arch + Rendering

- [x] SIMD/SIMT, warp/wavefront scheduling, divergence
- [x] Memory hierarchy: regs → shared/local → L1/L2 → global; coalescing
- [ ] Memory subsystem design tradeoffs (banking, bus width, cache size)
- [ ] Rendering pipeline: vertex → rasterize → fragment shade → framebuffer
- [ ] Z-buffer / depth test
- [ ] Texturing + texture memory access
- [ ] Why fragment shaders map well onto SIMT

## 3. Comp Arch (fast refresh)

- [x] Pipelining: hazards, forwarding, stalls
- [x] Caches: locality, associativity, tag/index/offset, LRU, coherence
- [ ] Interrupts/exceptions
- [ ] Memory ordering / consistency

## 4. DV Mindset

- [ ] Restate the spec
- [ ] ID state + transitions
- [ ] Model it
- [ ] List test cases: normal / boundary / corner / invalid
- [ ] What could go wrong
- [ ] How to check correctness
- [ ] Practice on: FIFO, arbiter, interrupt controller, cache

## 5. Verification

- [x] Testbench: DUT, stimulus, checker/scoreboard, ref model
- [x] Constrained-random testing
- [x] Functional coverage

## 6. Verilog/SV

- [x] Module structure: ports, params, instantiation
- [x] `always @(posedge clk)` vs `always @(*)`
- [x] Blocking (`=`) vs non-blocking (`<=`)

## 7. UVM (low priority)

- [ ] Driver / monitor / sequencer / agent / scoreboard / env
- [ ] Sequence / sequence item
- [ ] Factory pattern / config_db

## 8. Coding Warm-Up

- [ ] Arrays + bit manipulation
- [ ] Binary vs linear search
- [ ] Big-O — state and justify
- [ ] One DFS/BFS-flavored pass

## Friday AM Cram

- [ ] Resume, out loud, no notes
- [ ] Comp arch cheat sheet
- [ ] GPU/rendering one-pager
- [ ] DV mindset re-read