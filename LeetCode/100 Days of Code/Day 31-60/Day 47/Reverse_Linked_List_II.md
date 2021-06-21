# [92. Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)

## Solutions

### Solution 1

```
var reverseBetween = function(head, left, right) {
    let dummy = new ListNode(0, null)
    dummy.next = head
    let node = dummy
    let i=1
    while(i<left){
        node = node.next
        i++
    }
    
    let start = node
    let end = node.next
    node = node.next
    let curr = null
    while(i<=right){
        let temp = node.next
        node.next = curr
        curr = node
        node = temp
        i++
    }
    start.next = curr
    end.next = node
    return dummy.next
};
```

TC: O(n)
SC: O(1)