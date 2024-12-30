---
layout: post
title: "Python Cheat Sheet for Coding Test"
css: styles.css
---


## Python Cheat Sheet for Coding Test

#### Basic
Merge int number into string
```python
a = [1, 2, 3, 4, 5]
''.join(str(e) for e in a)
''.join(map(str, a))
```


***
#### Palindrome
Time Complexity = O(n)
```python
q = [1, 2, 3]
if q.pop(0) != q.pop():
    return False 
```

Time Complexity = O(1)
```python
q = [1, 2, 3]
q = collections.deque()
if q.popleft() != q.pop():
    return False
```

***
#### Linked List
Merge two sorted lists
```python
def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    if (not list1) or (list2 and list1.val > list2.val):
        list1, list2 = list2, list1
    if list1:
        list1.next = self.mergeTwoLists(list1.next, list2)
    return list1
```

Reverse Linked List
```python
def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
    node = head
    prev = None

    while node:
        next_node, node.next = node.next, prev
        prev, node = node, next_node
    
    return prev
```

Swap nodes in pairs
```python
def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
    cur = head
    while cur and cur.next:
        cur.val, cur.next.val = cur.next.val, cur.val
        cur = cur.next.next
    return head
```

Odd even linked list
```python
def oddEvenList(self, head: ListNode) -> ListNode:
    if not head or not head.next:
        return head
    
    odd = head
    even = head.next
    even_head = head.next

    while even and even.next:
        odd.next, even.next = odd.next.next, even.next.next
        odd, even = odd.next, even.next
    
    odd.next = even_head
    return head
```
Reverse linked list (from left to right)
```python
def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
    if not head or right == left:
        return head
    
    root = start = ListNode(None)
    root.next = head

    for _ in range(left - 1):
        start = start.next
    end = start.next

    for _ in range(right - left):
        tmp, start.next, end.next = start.next, end.next, end.next.next
        start.next.next = tmp
    
    return root.next
```


