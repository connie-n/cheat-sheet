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


- [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
```python
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        root = result = ListNode(None)
        heap = []

        for i in range(len(lists)):
            #add the first value of node(lists[i].val), index(i), node(lists[i])
            if lists[i]:
                heapq.heappush(heap, (lists[i].val, i, lists[i]))
            
        while heap:
            node = heapq.heappop(heap) #extract minimum node
            idx = node[1] #original index of list
            result.next = node[2] #set result.next as current node

            result = result.next #move result pointer to next
            if result.next: #if there is next node, add to heap
                heapq.heappush(heap, (result.next.val, idx, result.next))

        return root.next 
```

- [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

**heapq.nlargest(n, iterable, key=None)**
Return a list with the n largest elements from the dataset defined by iterable. key, if provided, specifies a function of one argument that is used to extract a comparison key from each element in iterable (for example, key=str.lower). Equivalent to: sorted(iterable, key=key, reverse=True)[:n].

**heapq.nsmallest(n, iterable, key=None)**
Return a list with the n smallest elements from the dataset defined by iterable. key, if provided, specifies a function of one argument that is used to extract a comparison key from each element in iterable (for example, key=str.lower). Equivalent to: sorted(iterable, key=key)[:n].


```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        cnt = collections.Counter(nums)
        #return [num for num, freq in cnt.most_common(k)]
        return heapq.nlargest(k, cnt.keys(), key=cnt.get)
```


- [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
```python
class MedianFinder:
    def __init__(self):
        self.low = [] #maxheap
        self.high = [] #minheap
        
    def addNum(self, num: int) -> None:
        heapq.heappush(self.low, -num)
        heapq.heappush(self.high, -heapq.heappop(self.low)) #max value of maxheap to minheap
        
        if len(self.low) < len(self.high):
            heapq.heappush(self.low, -heapq.heappop(self.high))

    def findMedian(self) -> float:
        if len(self.low) > len(self.high):
            return -self.low[0] #return max value of maxheap when len is odd
        return (-self.low[0] + self.high[0]) / 2.0
```

- [Total Cost to Hire K Workers](https://leetcode.com/problems/total-cost-to-hire-k-workers/)

```python
class Solution:
    def totalCost(self, costs: List[int], k: int, candidates: int) -> int:
        n = len(costs)
        left_heap = []
        right_heap = []
        left = 0
        right = n - 1
        sumcosts = 0

        for _ in range(min(candidates, n)):
            heapq.heappush(left_heap, (costs[left], left))
            left += 1

        for _ in range(min(candidates, n - left)):
            heapq.heappush(right_heap, (costs[right], right))
            right -= 1

        for _ in range(k):
            # select smaller value in the right and left heaps 
            if right_heap and (not left_heap or left_heap[0] > right_heap[0]):
                cost, idx = heapq.heappop(right_heap)
                if right >= left: # add new worker
                    heapq.heappush(right_heap, (costs[right], right))
                    right -= 1     
            else:
                cost, idx = heapq.heappop(left_heap)
                if left <= right:
                    heapq.heappush(left_heap, (costs[left], left))
                    left += 1 
                    
            sumcosts += cost

        return sumcosts 
```

- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

Use heapify
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        heapq.heapify(nums)
       
        kth_largest = (heapq.nlargest(k, nums))
        return kth_largest[k-1] #heapq.nlargest(k, nums)[-1]
```

Use sort 
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        return sorted(nums, reverse=True)[k-1]
```

<br>   



