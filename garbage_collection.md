## Business Case

No matter how powerful your machines are, wasted memory is wasted money.
In many workloads, memory usage may spike briefly during specific phases of execution.
If we understand how to control or influence garbage collection, we may be able to
avoid provisioning unnecessarily large machines solely to accommodate those 
short-lived spikes.

## Idea

Garbage collection is an automatic memory-management mechanism. While the mutator is
running, it continually allocates memory from the heap. When it requires more memory
than is currently available, the garbage collector reclaims unused memory and returns
it to the heap.

## Details
``` python
item = []
message_q = []
for i in range(10):
  message_q.append(item)
# inspecting the refernce count value for object item
import sys
sys.getrefcount(item)
```
In this application code example,the python standard library function list.append function has instruction in it's program
to increment the object reference counter by one.

## Understanding check
What will be the output of print(sys.getrefcount(item)) and print(sys.getrefcount(message_q))
## Answer
12 \
2
## Explanation
when item is appended to message_q the following happens:
 - message_q[0] refers to item
 - message_q[1] refers to item ... and so own till the 10th message_q list-item refers item
 - therefore now 10 objects refers to item object therefore 10
 - 12 is because at creation reference count is set to 1 by convention and
   next 1 is because we called sys.getrefcount so the argument variable refernce
   
refer:
- [The macro that is used in the list implementation source code to do this count keeping](https://github.com/python/cpython/blob/1fb72d2ad243c965d4432b4e93884064001a2607/Include/object.h#L782)
- [macro](https://gcc.gnu.org/onlinedocs/cpp/Macros.html)
