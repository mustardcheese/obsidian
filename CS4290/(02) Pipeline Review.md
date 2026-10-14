## Datapath Options

- **Multi-cycle**: simple datapath + microcode → several cycles/instr (even NOP = 3)
- **Single-cycle**: CPI = 1, but clock must fit the **slowest** instruction
- **Pipelined**: IF → ID → EX → MEM → WB, latch between stages → 1 instr/cycle after warm-up

## Latency vs Throughput

|Stage|IF|ID|EX|MEM|WB|
|---|---|---|---|---|---|
|Time|1.0|0.6|0.9|1.2|0.4 ns|

|Design|Cycle time|Inst latency|
|---|---|---|
|1-stage|4.1 ns (**sum**)|4.1 ns|
|5-stage|1.2 ns (**max**)|6.0 ns|

- Latency ↑ (latches + longest stage sets clock), but **throughput** is the goal
- **Speedup = 4.1 / 1.2 ≈ 3.42** (ideal = 5)

## How Many Stages?

- Speedup ~ # stages → deep pipelines (Pentium 4, **>30 stages**)
- Limited by **dependences**:
    - **Control**: branch resolved in stage 32 → 32 cycles of fetch on unknown path
    - **Data**: `LW R1,0(R2)` value ready stage 40, `ADD R2,R3,R1` needs it stage 25 → **15-cycle stall**