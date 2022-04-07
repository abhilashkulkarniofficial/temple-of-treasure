# Linked List

## LL Node

```
class ListNode(object):
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

## Reverse LL

```
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        prev = None
        node = head
        
        while node != None:
            temp = prev
            prev = node
            node = node.next
            prev.next = temp
            
        return prev
```

## Merge 2 list:

```
class Solution(object):
    def merge2List(self, list1, list2):
        prehead = ListNode(-1)
        
        prev = prehead
        
        while list1 and list2:
            if list1.val <= list2.val:
                prev.next = list1
                list1 = list1.next
            else:
                prev.next = list2
                list2 = list2.next
                
            prev = prev.next
            
        prev.next = list1 if list1 is not None else list2
        
        return prehead.next
```

## Merge k lists:

Divide and Conquor Approach

```
class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        a = len(lists)
        interval = 1
        
        while interval < a:
            for i in range(0, a - interval, interval * 2):
                lists[i] = self.merge2List(lists[i], lists[i+interval])
            interval *= 2
            
        return lists[0] if a > 0 else None
        
        
    def merge2List(self, list1, list2):
        prehead = ListNode(-1)
        
        prev = prehead
        
        while list1 and list2:
            if list1.val <= list2.val:
                prev.next = list1
                list1 = list1.next
            else:
                prev.next = list2
                list2 = list2.next
                
            prev = prev.next
            
        prev.next = list1 if list1 is not None else list2
        
        return prehead.next
```

Priority Queue method:

```
class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        head = curr = ListNode(0)
        q = PriorityQueue()
        
        for l in lists:
            if l:
                q.put((l.val, l))
                
        while not q.empty():
            val, node = q.get()
            curr.next = ListNode(val)
            curr = curr.next
            node = node.next
            if node:
                q.put((node.val, node))
                
        return head.next
```

## Remove nth node from the end

```
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        dummy = ListNode(-1)
        dummy.next = head
        node1 = dummy
        node2 = dummy
        
        for _ in range(n+1):
            node1 = node1.next
            
        while(node1 != None):
            node1 = node1.next
            node2 = node2.next

        node2.next = node2.next.next

        
        return dummy.next
```

## Reorder List

```
class Solution(object):
            
    
    def reorderList(self, head):
        """
        :type head: ListNode
        :rtype: None Do not return anything, modify head in-place instead.
        """
        if not head:
            return 
        
        # find the middle of linked list [Problem 876]
        # in 1->2->3->4->5->6 find 4 
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next 
            
        # reverse the second part of the list [Problem 206]
        # convert 1->2->3->4->5->6 into 1->2->3->4 and 6->5->4
        # reverse the second half in-place
        prev, curr = None, slow
        while curr:
            curr.next, prev, curr = prev, curr, curr.next       

        # merge two sorted linked lists [Problem 21]
        # merge 1->2->3->4 and 6->5->4 into 1->6->2->5->3->4
        first, second = head, prev
        while second.next:
            first.next, first = second, first.next
            second.next, second = first, second.next

```