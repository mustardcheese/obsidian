
Why do I want threading?
- Allows for concurrency and multiprocessing

Why multiprocessing vs multithreading?
- Switching between threads can be very lightweight

We can still achieve concurrency with things like asynchronus

Additional threading benefits?
- Organization of code, makes it more modular, easier to process asynchronous events
- Threads give us abstraction of concurrency

## Abstraction of Concurrency

Threading is a mechanism to create concurrency
- The abstraction of concurrency is the ability to seamlessly execute independent threads of execution at the same time

Mechanisms of Concurrency:
- Threads
- Multi-processing
- Event-based systems

### Multiprocessing
- Share compute resource but not memory
- **Guarantee:** memory space isolation

### Threads
- Purposefully break isolation
- **Guarantee:** shared memory resources by design

"thread of execution is the smallest sequence of programmed instruction that can e managed independently by a scheduler"

**Benefits of Threads**
- Responsiveness (provide abstraction of concurrency)
- Resource sharing (shared processing + memory)
- Economy (less overhead)
- Multiprocessing (achieve near-true parallelism)
---

## Threading Design

### One-to-One (1:1) -- Kernel Threading
![[Pasted image 20260303143530.png|500]]
- We allow each kernel thread to map to one user thread
- Improved concurrency
- Can run processor in parallel on multiprocessor
- Downside: Limited physically by processor
	- If we have 32 processor (kernel) threads, it mean we can only support 32 user threads too
- Overhead: We must first create a kernel thread for each user thread
	- Computational overhead by the scheduler
	- Memory overhead


### Many to One -- User Space Threading
![[Pasted image 20260303143619.png|500]]
Maps many user threads to one kernel thread
- The application knows more about the threads it wants to schedule than the kernel
	- Design advantage
- Simple, efficient
- Downside: true concurrency is difficult, since only one kernel thread controls resources, user threads can back each other up
- Only one thread can access a kernel at a time, so no true parallelism can be achieved

**watch the lectures for exam, tosses out all sorts of questions**

Concurrency is an abstraction
- Multiple mechanisms to acheive it
- The illusion of making concurrent progress on multiple execution streams
Parallelism (True Parallelism)
- Act of executing something truly in parallel
- Simultaneous execution of multiple execution streams
- Concurrency mechanisms can be used to leverage parallelism

Kernel-Space
- Parallelism
- Preemption possible
- More info given to the kernel
- Ability to control resource utilization
User-Space
- Semantically-aware scheduling (application aware)
- Context switching overhead
- Cache locality
- Lighter weight than kernel threading
- Overhead of thread creation (more in terms of user-space, no overhead in terms of kernel-space)


for example in user space:
- 1 thread runs then executes sleep(100)
- 1 thread continues to run in the meantime
sleep causes kernel thread to switch and lose focus -- that second thread never gets to run even though the other thread called sleep

### Many to Many -- Hybrid Threading
![[Pasted image 20260303150242.png|500]]
In theory, it gives the best of both worlds, making semantic-aware threads and true parallelism