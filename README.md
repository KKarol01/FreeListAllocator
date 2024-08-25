# Free list allocator
Uses in-memory headers and linked list for free blocks. Aligned to alignof(max_align_t). Doesn't support allocations with alignment greater than that.
Doesn't free the pool's memory on instance destruction.

## How to use:
```c++
void* pool = malloc(1024);
FreeListAllocator alloc{pool, 1024};

void* p1 = alloc.allocate(100);
void* p2 = alloc.allocate(324);
if(p1) { memset(p1, 0, 100); }
alloc.deallocate(p1);
alloc.deallocate(p2); // p2 can be nullptr

free(pool);
```
