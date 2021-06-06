# [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

## Solutions

### Solution 1

```
var middleNode = function(head) {
    let len = 0
    let node = head
    while(node){
        len++
        node = node.next
    }
    let mid = parseInt(len/2)
    node = head
    while(mid){
        node = node.next
        mid--
    }
    return node
};
```

Time complexity : O(n) + O(n/2) = O(n)
Space complexity : O(1)

### Solution 2

Using 2 pointer approach. 
Slow pointer: starts at head, moves at a distance of 1
Fast pointer: starts at head, moves at a distance of 2
By the time fast pointer reaches the end, slow pointer reaches middle.

```
var middleNode = function(head) {
    let slow = head
    let fast = head
    while(fast && fast.next){
        slow = slow.next
        fast = fast.next.next
    }
    return slow
};
```

TC: O(n/2)
SC: O(1)
