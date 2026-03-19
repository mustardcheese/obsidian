Task: Re implement gslib's [crystal router](https://arxiv.org/pdf/1404.3321) defined in
https://github.com/Nek5000/gslib/blob/master/src/crystal.c

into MFEM such that it will not require gslib as a dependency.

### Usages of gslib's crystal router
```c++
crystal_init
crystal_free
```
- fem/particleset.cpp
- fem/particleset.hpp
- fem/gslib.cpp
- fem/gslib.hpp


# Claude Plan
### Phase 1: Build the new crystal router
  1. Create general/crystal.hpp — Define a CrystalRouter class (or just free functions) that holds an MPI_Comm and two work buffers. This is the MFEM-native replacement for gslib::crystal.

  2. Implement the core hypercube routing algorithm — Port the crystal_router() function from crystal.c (the while(n>1) recursive bisection loop). Use MPI_Isend/MPI_Irecv directly instead of gslib's comm_isend/comm_irecv. The message buffer format ([target, source, length,...payload...] as uint arrays) can stay the same internally.
  
  3. Implement sarray_transfer equivalent — A templated function that:
	  - Sorts elements by destination proc (use std::sort or a permutation sort)
	  - Packs POD structs into the integer message buffer (port pack_int/pack_ext)
	  - Calls the hypercube router
	  - Unpacks received messages back into the array (port unpack_int)
	  - Resizes the output array to the received count   

  - 4. Implement sarray_transfer_ext equivalent — Variant where the destination proc is in a separate external array rather than a struct field. 
  
  - 5. Replace sarray_sort usage — Either provide a small utility or just use std::sort with a lambda at each call site. There are only a few sarray_sort calls.

### Phase 2+:
Phase 2: Replace gslib types with MFEM types                                                                                                   
  - 6. Replace struct array with mfem::Array<T> — At each call site in gslib.cpp and particleset.cpp, the gslib struct array (type-erased {void  
  *ptr, size_t n, max}) gets replaced with a typed mfem::Array<T>. The POD struct definitions (srcPt_t, outPt_t, etc.) can stay as-is. Note:
  mfem::Array<T> already requires std::is_trivial<T>, so POD structs work.                                                                       
  - 7. Replace gslib::comm with direct MPI_Comm — Every use of gsl_comm->c becomes the stored MPI_Comm, gsl_comm->id becomes an MPI_Comm_rank
  call (or a cached int), and gsl_comm->np becomes MPI_Comm_size. The classes already receive MPI_Comm in their constructors.                    
  - 8. Remove gslib::crystal *cr members from FindPointsGSLIB — Replace with your new CrystalRouter (or just MPI_Comm if your transfer functions
  are stateless apart from the communicator). Same for OversetFindPointsGSLIB and GSOPGSLIB.                                                     
  - 9. Remove gslib::crystal *cr from ParticleSet — Same treatment in particleset.hpp / particleset.cpp.
  
  Phase 3: Update call sites in gslib.cpp                                                                                                        
  - 10. Update FindPointsGSLIB constructors/destructor — Remove crystal_init/crystal_free/comm_init/comm_free calls. Replace with constructing   
  your new router (or just storing MPI_Comm).
  - 11. Port DEV.cr usage — DEV.cr points into gslib's internal findptsData structure. The sarray_transfer calls using DEV.cr need to use your   
  new function instead. You'll need to understand whether DEV.cr shares the same communicator as cr (it does — it's the crystal router embedded  
  in the findpts data).
  - 12. Convert each sarray_transfer call site (~12 in gslib.cpp) — Mechanically replace each one. The pattern is always:                        
  // Before:                                                                                                                                     
  sarray_transfer(struct outPt_t, &out_pt, proc, 1, cr);
  // After:                                                                                                                                      
  CrystalTransfer(comm, out_pt_array, offsetof(outPt_t, proc), true);
  - 13. Convert sarray_transfer_ext call in particleset.cpp — The particle redistribution path uses the _ext variant with an external proc array.
  - 14. Convert array_init/array_reserve/array_free calls — Replace with mfem::Array<T> construction, SetSize/Reserve, and automatic destruction.
  
  Phase 4: Update GSOPGSLIB                                                                                                                                                                                             
  - 15. Update GSOPGSLIB constructor/destructor — Remove gslib crystal/comm init/free. Note: GSOPGSLIB also uses gslib_gs_setup/gslib_gs for     
  gather-scatter operations — those are separate from the crystal router. If you're only porting the crystal router and not the gather-scatter,
  GSOPGSLIB may still need gslib for gs_data.                                                                                                    

  Phase 5: Update build system and headers                                                                                                       
   
  - 16. Update gslib.hpp forward declarations — Remove the namespace gslib { struct crystal; struct comm; } forward declarations. Add #include   
  "general/crystal.hpp" or equivalent.
  - 17. Update particleset.hpp — Remove gslib::crystal *cr and gslib::comm *gsl_comm members.                                                    
  - 18. Update CMake — Add general/crystal.cpp to the build. Check whether any MFEM_USE_GSLIB guards around crystal router code need updating    
  (the crystal router should now work without gslib being installed, but other gslib features like findpts and gs still need it).                

  Phase 6: Test                                                                                                                                  

  - 19. Build and run existing gslib tests — tests/unit/fem/test_gslib.cpp and the gslib miniapps (miniapps/gslib/) exercise the crystal router  
  paths. They should produce identical results.
  - 20. Test round-trip correctness — Verify that two consecutive CrystalTransfer calls return data to its original rank (the set_src round-trip 
  property).                                                                                                                                     
  - 21. Test at various rank counts — The hypercube algorithm has edge cases for odd rank counts and power-of-2 vs non-power-of-2. Test with 1,
  2, 3, 4, 7, 16 ranks.                           
