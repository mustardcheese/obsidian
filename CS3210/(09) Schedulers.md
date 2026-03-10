We need schedulers when:

- There are multiple resource consumers
- A scarce set of resources are being shared
- This is **multiplexing**

## Scheduling Motivation

Schedulers are one of the OS mechanisms that enable:
- Process Isolation
- Resource Multiplexing
    - Fairness
    - Resource Utilization

What do schedulers schedule? Processes, Disk I/O, Networking, Cloud Systems, AI workloads, etc.

Goal of a scheduler: **Maximize the amount of work we care about**

## Scheduling Goals

**Throughput scheduling** (e.g., disk)

- Orders of magnitude performance difference as f(access pattern)
- Elevator scheduling — implicit assumption of **actuation delay** (physical seek cost), so batch nearby requests
    - Declarative requests (Coda elevators): declare intent, system optimizes route

**Minimize response time** — e.g., social media feed, want minimal user-perceived delay

**Maximize latency SLO attainment** — e.g., ad serving, LLM inter-token latency, AR/VR

- SLO = Service Level Objective (e.g., "99% of requests ≤ 36ms")
- **Tail latency** = latency at a high percentile (e.g., 99th %ile on the CDF)
- PDF: y = P(X = x) | CDF: y = P(X ≤ x)

**Minimize cost** — dollar cost, energy, etc.

## Systems Conjecture

**Can't have all three of: simplicity, performance, cost** — pick two.
![[Pasted image 20260310171419.png]]
## Scheduling Design Space

| Dimension                  | Tradeoff                                                                                |
| -------------------------- | --------------------------------------------------------------------------------------- |
| Throughput vs. Latency     | Batching helps throughput, hurts latency                                                |
| Fairness                   | Time quotas, epochs; hard in heterogeneous contexts                                     |
| QoS                        | Priority levels (e.g., `nice`)                                                          |
| Preemptive vs. Cooperative | OS forces yield vs. process volunteers                                                  |
| Global vs. Local           | Full resource visibility vs. scalable but partial view                                  |
| Scalability                | Can it handle 1M processes? Scheduler complexity matters                                |
| Granularity (quantum)      | 10ms (responsive, more overhead) vs. 100ms (less overhead, less responsive) vs. dynamic |
| Constraints                | Real-time deadlines (e.g., airplane control)                                            |

**No perfect/universal policy.** Contradicting goals:

- Maximizing throughput vs. minimizing latency
- Minimizing response time vs. maximizing scalability
- Maximizing fairness vs. maximizing scalability
- Maximizing resource utilization vs. minimizing power consumption

## Scheduling Scenarios

Long-running jobs → **FCFS** can work (low context switch overhead, order matters less) Short-running jobs → **Preemptive** scheduling better (avoid head-of-line blocking)

## Scheduling Costs & Benefits

**Costs:**
- Context switching (register save/restore + **cache pollution**)
- Scheduler algorithm time complexity
- Loss of predictability (critical for RTOS)

**Benefits:**

- Better resource utilization
- Priority allocation to higher-value work
- Stronger QoS guarantees

## Process Characterization

|Type|Behavior|Scheduling Need|
|---|---|---|
|CPU-bound|Hogs CPU continuously|Can tolerate longer quanta, gets deprioritized in Linux|
|I/O-bound|Sleeps often (waiting on I/O)|Needs fast response when ready, gets boosted in Linux|
|Interactive|e.g., vim, emacs|Low latency critical|
|Batch|e.g., cronjob|Throughput matters, latency doesn't|
|Real-time|e.g., audio, video, AR/VR, chatbot|Needs both throughput (qps) AND latency (e.g., TBT)|

## Round-Robin

**Pros:** Simple (fixed time unit per process), starvation-free (no priority)
**Cons:** No urgency/priority distinction, deadline-unaware, doesn't handle throughput vs. latency disparity
![[Pasted image 20260310171535.png]]

## Linux Scheduler

**Motivating Observation:** Processes that constantly use full CPU are likely lower priority than those that mostly sleep (e.g., network servers need fast turnaround but sleep most of the time)

**Idea:** Reduce priority from CPU-hogging processes → dynamic priority adjustment

**Weighted Fair Queuing (WFQ):** Share resources proportionally to process weight

- Process A (weight 2) + Process B (weight 1) → A gets 2/3 CPU, B gets 1/3
- **CFS** (Completely Fair Scheduler) is Linux's implementation of WFQ
- If a process sleeps, it falls behind on virtual runtime → gets boosted when it wakes up
![[Pasted image 20260310171553.png]]

### Linux Scheduling Policies

|Policy|Use|
|---|---|
|`SCHED_OTHER`|Default time-sharing (CFS)|
|`SCHED_IDLE`|Very low priority background|
|`SCHED_BATCH`|CPU-intensive batch jobs|
|`SCHED_FIFO`|Real-time FIFO (runs until yield/preempted by higher RT)|
|`SCHED_RR`|Real-time round-robin (FIFO + time quanta among same-priority)|

RT policies (`FIFO`, `RR`) always preempt normal policies.

## Real-Time Scheduling

**Hard** real-time — must complete within guaranteed time bound

- Impractical with secondary storage / virtual memory — page faults and disk access introduce **unpredictable, unbounded latency**

**Soft** real-time — critical tasks get priority over less critical

- Requires: (1) priority scheduling (urgency-aware), (2) low dispatch latency
- Low dispatch latency is hard — e.g., many OSes can't preempt system calls mid-execution
