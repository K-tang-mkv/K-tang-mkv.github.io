# Heap in C++

A heap is a data structure that has the form of a tree and that respects the heap property, namely: every node must be lower than each of its children.

I suppose that the name “heap” comes from the fact that if you pile up a heap of stuff, you’d rather put the big things at the bottom and the small at the top if you want it to hold:

![heap metaphor](/assests/heap.png)

### Max heaps

The heap property, that every node must be lower than its children, can be generalized to another comparison than “lower than” as in operator<. We could use a certain relation that makes more sense for the data type that is in the heap. For instance, a heap of sets could use a lexicographical relationship.

In particular, we can also use the relation “greater than” in the heap property (which can still be implemented by using operator< by turning around the heap property and ensuring that children are lower than their parents).

Such a heap is called a max heap, and this is the sort of heap that the STL has. So by heap I will mean binary max heap throughout this article.

In a max heap, the largest element is at the root. So here is an example of a heap:

![heap1](/assests/heap1.png)

### Implementing a heap
To represent a binary tree such as a heap, one implementation is to make a dynamic allocation for each node, with 2 pointers pointing to its children.

But there is a much more efficient (and elegant) implementation: representing it in the form of an array, by doing a level order traversal of the heap. Said differently, it means that the array starts with the element at the root, then follows with the children of that root, then all the children of those children. And then the great-grand-children. And so on.

This way, the greatest element is at the first position of the array.

This animation illustrates how to above heap could be represented as an array:

![heapgif](/assests/heap.gif)

This is how the STL represents heaps: a heap can be stored in an std::vector for example, with the elements laid out next to each other like above.