## HEAPS AND PRIMARY QUEUE




## 🛠 Index

-  [💡 Primary queue](#-Primary-queue)
- [💡 Heaps](#-Heaps)
-  [🃏 Leetcode](#-Leetcode)


## 💡 Primary queue
> (_Reference: Data Structures The Fun Way_)
>- use an additional piece of information to determine the retrieval order (the item's priority)
>- new information allow us to further adapt to the data and, among other useful applications, allow us to process urgent requests first
>- priority queue store a set of items and enable the user to easily retrieve the item with the highest priority. 
>- we need to be able to add and remove items from our prioritized task list.  
>- in their most basic form, priority queues support a few primary operations:
>   - add an item and its associated priority score.
>   - look up the item with the highest priority (or null if the queue is empty)
>   - remove the item with the highest priority (or null if the queue is empty)



## 💡 Heaps  
**Max heaps**
> (_Reference: Data Structures The Fun Way_)
>- a max heap is a variant of the binary tree that maintains a special ordered relationship between a node and its children. 
>- specially, a max heap stores the elements according to the max heap property, which states that the value at any node in the tree is larger than or equal to the values of its child nodes. 


- In the array-based implementiation, child node indexes are defined relative to the indexs of their parents, so a node at index _i_ has children at indexes _2i_ and _2i+1_. 
- Adding elements, removing the highest-priority elements from heaps, sorting auxiliary information, updating priorities



**Min heaps**
>- (_Reference: Data Structures The Fun Way_)
>- the min heap is a version of the heap that facilitates finding the item with the lowest value. 
>- the min heap property is that the value at any node in the tree is smaller than (or equal to) the values of its children. 

- Adding and removing elements


**Heapsort**
>- (_Reference: Data Structures The Fun Way_)
>- heapsort is an algorithm for sorting a list of item using the heap data structure. 
>- the input is an unsorted array. the output is an array containing those same elements, but in decreasing sorted order(for a max heap)





## 🃏 Leetcode

### 

- [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)


   
<br>   




