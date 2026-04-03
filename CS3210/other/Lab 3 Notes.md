Skeleton & Order                                                                       
   
  Phase 1: Plumbing (syscall wiring)                                                   

  Files: include/syscall.h, kernel/src/syscall.c, user/asm/usys.S                        

  - Add SYS_clone (and later SYS_waitpid, SYS_park, SYS_setpark, SYS_unpark) to the syscall number table                                                                 
  - Wire them into the dispatch array in syscall.c                                       
  - Add SYSCALL(clone) etc. in usys.S                                                    
  
  Phase 2: Thread group tracking in struct proc                                          
      File: kernel/include/proc.h                                                            
                                                                                       
  - You need to figure out what fields to add so threads know they're in a group and     
  share resources. Think about: who owns the page directory? How do you reference-count
  shared resources so only the last thread frees them? How does exit() / wait() change?  
                  
  Phase 3: Core clone() implementation

  File: kernel/src/proc.c (new function), kernel/src/sysproc.c (thin sys_clone wrapper)  
  
  - Similar to fork() but instead of copyuvm(), you share the parent's pgdir             
  - Instead of filedup/idup per-thread, threads share the same fd table and cwd (pointer
  sharing, not copying)                                                                  
  - The tricky part the README warns about: stack setup. You can't just memcpy the stack
  — you need to relocate frame pointers (%ebp chain) so the child's backtrace walks its  
  own stack, not the parent's. Think back to lab1 backtrace.
  - Set child's %eax to 0 (return value), parent gets child pid                          
                                                                                         
  Phase 4: Adjust exit(), wait(), and VM teardown                                        
                                                                                         
  Files: kernel/src/proc.c, kernel/src/vm.c                                              
                  
  - freevm() currently frees the page directory unconditionally — with shared address    
  spaces, only the last thread should free it
  - exit() needs to handle thread group membership (close files only if last thread,     
  etc.)                                                                                  
  - Implement waitpid() so you can wait on a specific thread
                                                                                         
  Phase 5: User-space thread library
                                                                                         
  File: user/src/threads.c                                                               
  
  - thread_create(): allocate a stack (e.g., via sbrk), call clone(stack, size), handle  
  return          
  - thread_wait(): call waitpid() on the thread's pid                                    
  - Note free_stack_and_exit.S exists for safely freeing a thread's stack before exiting 
  — you'll need to understand when/how to use it                                         
                                                                                         
  Phase 6: Synchronization primitives (park/unpark, then mutexes/condvars)               
                  
  Files: kernel/src/proc.c, kernel/src/sysproc.c, user/src/threads.c                     
                  
  - Kernel-side park, setpark, unpark syscalls (sleep/wake mechanism for threads)        
  - User-space mutex_init/acquire/release and cond_init/wait/signal built on top
                                                                                         
  ---                                                                                    
  Estimated Effort                                                                       
                                                                                         
  ┌────────────────────────┬────────────────────────────────────────────────────────┐
  │         Phase          │                       Rough size                       │    
  ├────────────────────────┼────────────────────────────────────────────────────────┤
  │ 1 - Plumbing           │ Small, mechanical                                      │    
  ├────────────────────────┼────────────────────────────────────────────────────────┤
  │ 2 - Struct design      │ Small but think carefully — wrong design here cascades │    
  ├────────────────────────┼────────────────────────────────────────────────────────┤    
  │ 3 - Core clone         │ Medium-large, the stack relocation is the hard part    │    
  ├────────────────────────┼────────────────────────────────────────────────────────┤    
  │ 4 - exit/wait/VM fixes │ Medium, subtle reference-counting bugs live here       │
  ├────────────────────────┼────────────────────────────────────────────────────────┤    
  │ 5 - Thread library     │ Small-medium                                           │
  ├────────────────────────┼────────────────────────────────────────────────────────┤    
  │ 6 - Synchronization    │ Medium                                                 │
  └────────────────────────┴────────────────────────────────────────────────────────┘    
                  
  Phase 3 and 4 are where most of the debugging time will go. The stack pointer          
  adjustment logic and the shared-resource lifecycle are the two hardest conceptual
  pieces.