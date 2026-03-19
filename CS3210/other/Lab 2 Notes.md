# kalloc.c
- Where we keep the main struct for CoW
	- Array that keeps track of number of references to each (physical) page
	- Lock, and lock tracker
```
		struct {
		  int pageRefCount[PHYSTOP / PGSIZE];
		  struct spinlock lock;
		  int use_lock;
		} CoW;
```


```
kalloc() will set refcount to 1
kfree() will set refcount to 0
getrefcount()
increfcount() --- all to interact with struct
decrefcount()

kinit2() changed to zeroalloc
```

# flags
9th bit (PTE_nine) = CoW bit, if set means need to CoW
10th bit (PTE_ten) = zero bit, if set means is a zero-allocated page
write bit (PTE_W) = write bit, turned off for CoW and Zero because when we try to write, we get a page fault and we deal with it in our trap handler

every time we alloc out a page as CoW or zero, we need to set these flags

# zero-alloc
allocuvm() maps everything

# trap handler
extra checks in page faults for
- zero (PTE_ten) to kalloc out a real page
- cow (PTE_nine) does a reference count check to determine what needs to be recopied -- if ref == 1, just change flags
invalidates tlb along the way

# deallocuvm
- checks if a page is zero mapped before freeing


# loaduvm
  - loaduvm: if it encounters a zero-page-mapped PTE while loading a binary, it allocates a real page first before writing program data.
  - copyout: same treatment — if copying data into a zero-page-mapped address (e.g., setting up argv), it materializes the page first.



  - walkpgdir() and mappages() changed from static to externally visible.
  - Added comments throughout proc.c (fork) and string.c explaining existing code.
  - Added mytests.c with a comprehensive suite of test scenarios (child/parent write, exec, pipe, grandchild, sibling forks, stack overflow guard
   page test).