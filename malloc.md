---
layout: default
---

# Dynamic Memory Allocator<br>(March 2024)

[Back to Main Page](../)

As part of the Computer Engineering facet of my degree, I took a class that had us build a custom version of the `malloc` function in C. The following is a description adapted from the assignment writeup.

This memory allocator is based on the segregated free lists scheme. In this scheme, multiple lists hold entries of open memory blocks that can be used for allocation. An array holds the head nodes of each list corresponding to a separate size range. The sizes are measured in words, and increase by powers of two; the 0th list holds free blocks of words 2<sup>1</sup> and up, the 1st list 2<sup>2</sup> and up, and so on. There are 12 such lists, and each list is a doubly-linked, non-circular list. Blocks are aligned to 8-byte boundaries.

To place a free block, blocks are sorted into the maximum possible list index; a block with 7 words could exist in the 0th list, but it would be placed in the 1st list. New free blocks replace the previous head of the list, creating a LIFO selection policy when combined with the selection scheme.

To select a free block, first the minimum index of the required size is calculated, then the head of that corresponding list is used. If there is no such list (the head does not exist), the next size up is used, and so on. For required sizes that are greater than the minimum guaranteed by the 11th list, the 11th list is searched for a block that can fit the required size, since any free block >2<sup>13</sup> will default to the 11th list.

Free blocks are split any time the requested size is less than the block's size, as long as the resulting block would meet the minimum size requirements.

Free blocks are coalesced at the earliest possible opportunity. This includes immediately after freeing a block and after expanding the heap.

This implementation enjoys improved time efficiency due to the LIFO organization of the free lists, as given that the lists are populated by free blocks, and the allocation is within the size limits of the lists, a block for allocation can be found in O(1) time. However, this scheme can cause fragmentation and reduce spacial efficiency, as the block chosen is simply the newest one, rather than a more strategic choice e.g. a block that fits the allocation perfectly and won't leave behind a smaller, less-useful free block.

When tested on the Rice University CLEAR servers, this function is capable of 42 million operations per second with 68% average utilization.
