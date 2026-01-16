# Memory Allocator Project Structure

```text
src/
  api/
    allocator.h          # Public allocator API (malloc/free-style)
    config.h             # Compile-time configuration flags

  core/
    align.h              # Alignment helpers
    math.h               # Power-of-two, size helpers
    stats.h
    stats.c              # Allocation / fragmentation metrics
    assert.h             # Debug assertions
    spinlock.h           # For future TLS / per-thread allocators
    platform.h
    platform.c           # OS abstraction (mmap/VirtualAlloc, page size)
    sanitizer.h
    sanitizer.c          # Poisoning, canaries (optional)

  ds/
    freelist.h           # Intrusive linked list utilities
    rb_tree.h
    rb_tree.c            # Red-black tree for tree-based free lists
    bitmap.h
    bitmap.c             # Buddy / slab bitmap helpers

  allocators/
    linear/
      linear.h
      linear.c
    stack/
      stack.h
      stack.c
    pool/
      pool.h
      pool.c
    freelist_ll/
      freelist_ll.c
    freelist_rbtree/
      freelist_rbtree.c
    buddy/
      buddy.c
    slab/
      slab.c
    segregated/
      segregated.c
    tls/
      tls.c               # Per-thread allocator (future)

  bench/
    bench_main.c
    workloads/
      microbench.c        # Simple alloc/free loops
      trace_replay.c      # Realistic allocation traces
      patterns.c          # Allocation patterns
    report/
      csv.c
      pretty_print.c

  tests/
    test_main.c
    unit/
      test_align.c
      test_rb_tree.c
    alloc/
      test_freelist.c
      test_buddy.c
```
## Design Notes
* api/ is the stable public interface
* core/ and ds/ contain reusable infrastructure shared across allocators
* Each allocator lives in its own directory to avoid cross-contamination.
* Benchmarks and tests are separated from allocator logic.
* Structure scales to TLS, hybrid allocators, and research-grade benchmarking.
