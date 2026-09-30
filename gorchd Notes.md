GPU over subscription is difficult because scheduling typically requires proprietary drivers.
This means varying levels of isolation, fairness, flexibility, and complexity
![[Pasted image 20260929235701.png|500]]


## How it works

![[Pasted image 20260930003608.png|700]]

### gorchd
is the daemon that polls using NVML API to check for usage within the GPU
- Opens a TCP socket for metrics, monitoring, and remote access
- munge authenticates TCP socket
- Collects GPU memory usage that belongs to a specific **UID**
- Enforce global **per-user** memory limit instead of per-process
- If user is over their memory quota, process is killed
- If user is over their usage quota, process is halted
**munge** provides authentication over that TCP socket

High Priority jobs run as normal via slurm within limits (upper bound memory quota)

**Reactive:**
gorchd -> *some signal SIGTERM (paper) / SIGKILL(diagram)* on the process
### gpu_fairshare_shim

Intercepts the LD_PRELOAD to check for memory usage, **only dynamically linked**
- throws a cudaErrorMemoryAllocation *as if* the system was out of memory
-  signals to gorchd that user is over the quota
- gorchd then exits from program
For SM processor usage, gpu_fairshare_shim simply sleeps until quota is unfilled

This only works for dynamically linked programs. Statically linked uses a different libraries unable to be intercepted by gpu_fairshare_shim

**Preventative:**
gpu_fairshare_shim (on dynamic) -> cudaErrorMemoryAllocation

## What to work on

### gpu_fairshare_shim VRAM usage
- intercept with a library that sits between program and cuda
- keep track internally (?)
- programs like pytorch still hold memory thats technically free, decide whether or not to include it

### gpu_fairshare_shim SM usage
- intercept with same library for compute usage
- allocate a budget

milestone: first build out the interception, next print out usage