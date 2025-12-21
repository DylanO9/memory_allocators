# Memory Allocators

## Context

**Stack**
: The stack is where local variables live for their temporary lifetime

**Heap**
: The heap is where variables with extended lifetimes live. Where dynamic memory lives

**Memory Allocator**
: A memory allocator manages the heap. In C, it is malloc and free.

## Different Type Of Allocators

### Linear Allocator
Idea: The linear allocator owns a chunk of memory. It uses a pointer to indicate the beginning of the memory. When making an allocation, the offset is the only value that changes. 

#### Components of a Linear Allocator:
- Base: The start of the owned chunk of memory
- Offset: The amount of memory that has been allocated
- Capacity: The size of the owned chunk of memory
 
#### Invariants
- Base always points to the start of the owned chunk of memory 
- 0 <= offset <= capacity

#### Allocate
Increment the offset to be right outside of the newly allocate dmemory.

#### Free
Can not free because there is not tracking being done

### Stack Allocator

### Pool Allocator

### Free List Allocator - Linked List

### Free List Allocator - Red Black Tree

### Buddy Allocator

### Slab Allocator

### Segregated Free List

### Two-Level Segregate Fit

### Cache-aware Allocator

### Hybrid / layered Allocator

### TLS / per-thread allocators 
