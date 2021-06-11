# [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

## Solutions

### Solution 1

```
var hasCycle = function(head) {
    let slow = head
    let fast = head
    while(slow && fast){
        slow = slow.next
        if(fast.next) fast = fast.next.next
        else return false
        if(slow===fast) return true

    }
    return false
};
```

TC: O(n)
SC: O(1)