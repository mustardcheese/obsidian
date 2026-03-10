:We need schedulers when:
- There are multiple resource consumers
- A scare set of resources are being shared

## Scheduling Motivation
Schedulers are one of the OS mechanisms that enable:
- Process Isolation
- Resource Multiplexing
	- Fairness
	- Resource Utilization

We know we need schedulers for multiplexing,
What else do they schedule?
- Processes
- I/O (Disk)
- Networking
- Cloud Systems
- AI

What is the goal of a scheduler? What is the measure of success?
- How much *stuff* a scheduler is able to do

## Scheduling Goals
Throughput Scheduling
- Orders of magnitude performance difference
- Elevator Scheduling
	- There's an implicit assumption of an actuation delay, so we want to move as little as possible
	- What about the CODA elevators?
- Scheduling to minimize response time
	- We want this to be as minimal as possible for the user
- Scheduling to maximize latency SLO attainment
	- Minimizing response time over an optimization setup

## Scheduling Scenarios
Imagine two different CPU scenarios:
- One with very long running jobs
	- We probably wouldn't want to use FCFS, it might cause starvation
- One with very short running jobs
	- We probably shouldn't use preemptive, we'll be switching a lot and preempting has lots of overhead
We need different schedulers in different scenarios

## Scheduler Design Considerations
What are the ***costs*** of scheduling
- Cost of interposing on control flow?
	- Context Switches
	- Caching costs
- Scheduler time complexity
- Predictability
What are the ***benefits*** of scheduling
- What do we get in return?

There is no perfect/universal solution/policy
- Maximizing throughput vs. minimizing latency
- Minimizing response vs. maximizing scalability
- Maximizing fairness vs. maximizing scalability
- Maximizing resource utilization vs. maximizing power consumption

### Round-Robin
Pros:
- Simplicity -- very easy, assign a fixed time unit per process
- No Starvation -- every process gets equal to processing time
Cons:
- Doesn't distinguish for urgency or priority of a process
- Deadline-unaware (lots of wait time)
- Doesn't handle disparity between throughput and latency

### Linux Scheduler

**Motivating Observation:**
Processes that constantly use full CPU are lower priority than those that mostly sleep
- Network servers need fast turn around time, but spend most of their time sleeping

**Reduce priority from processes that always consume CPU**
- Use CPU more -> Less CPU time (ur hogging the CPU bruh)
- Dynamic job scheduling

Weighted Fair Queuing -- Shares resources proportionally to process weight
- 2 Processes run, A with weight 2 and B with weight 1, A will get 2x resources as B
- CFS (what Linux uses) is an implementation of WFQ

### RTOS
**Hard** real-time -- Complete critical task within guaranteed time
- Embedded deployments in critical devices
- If this process doesn't run, someone will die
**Soft** real-time -- Critical receive priority over less critical

Hard real-time impractical with secondary storage or virtual memory
- Everything needs to be ultra predictable -- things like paging and traps aren't very predictable

Soft real-time has two requirements
- Priority scheduling (urgency aware)
- Low dispatch latency