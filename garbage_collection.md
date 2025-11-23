Business Case

No matter how powerful your machines are, wasted memory is wasted money.
In many workloads, memory usage may spike briefly during specific phases of execution.
If we understand how to control or influence garbage collection, we may be able to
avoid provisioning unnecessarily large machines solely to accommodate those 
short-lived spikes.

Idea

Garbage collection is an automatic memory-management mechanism. While the mutator is
running, it continually allocates memory from the heap. When it requires more memory
than is currently available, the garbage collector reclaims unused memory and returns
it to the heap.
