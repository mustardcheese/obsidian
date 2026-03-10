# Kernel Types
![[Pasted image 20260309212620.png|697]]
There are two main types of kernel: monolithic (left) and micro (right)
## Monolithic Kernel
![[Pasted image 20260309213700.png|600]]
- Everything is dependent on one large central kernel
- All user processes are built on top and run on top of the kernel, accessed by *syscalls*
- All dependencies, services, etc. handled by the kernel

**The kernel serves as the single massive point of weakness. All important services are run in *kernel space***

**Pros:**
- Very performative, User processes don't need to cross user-kernel boundary as often
- Everything (scheduling, file system, i/o) is all packaged into one place and handled through syscalls -- easier to make user space programs
- Simple calls: user process -> kernel syscall as necessary -> user process

Everything a user process might need lives within one large kernel (upside and downside)

**Cons:** 
- Low fault tolerance, a crash in the kernel might bring the entire operating system down with it
- Difficult to maintain such a large and complex object (kernel)
- Not modular at all, any changes must change the entire operating system
	- Linux has multiple versions of the same syscall because they can't just change an older version for compatability, so they have to add a new one entierly under a different name

**Great for speed, not great for safety

Linux (xv6 by extension), Windows are monolithic kernels

---
## Microkernel
![[Pasted image 20260310011634.png]]
- As little as possible is kept in the micro kernel as possible
- Nearly everything else not mandatory is run as a user space program
- Incredibly modular and simple kernel

Microkernel Architectures are the safest with the most isolation. The issue comes with crossing the kernel-user divide which comes with a lot of overhead, making the micro kernel slow

**Pros:**
    - Increased (failure) Isolation, if the file system fails, the rest of the kernel will work fine
    - Easy to extend and build upon
**Cons:**
    - Performance issues when crossing user/kernel boundary
    - Hard to compartmentalize
When key operating system

**Great for isolation, not great for speed**

macOS built on a micro kernel

--- 
## How do we build an operating system?
- Not all OS tasks belong inside the kernel
- How do we choose what belongs in the kernel?

Look at xv6’s system calls. There are 3 types of system calls
- Process, Memory, File system
- We depend on the kernel for isolation and protection, and inter process communication

### What is the kernel’s job? How is this different from the OS’s job?

Where do we draw the line between user and kernel space?

```bash
$echo Hello | cat
```

comprised of three processes:

- The shell which this runs on
- echo, forkexec’d by the shell
- cat, forkexec’d by the shell, connected by pipe

All three are within user space, but all 3 use syscalls and cross the kernel-user divide and interact with the kernel