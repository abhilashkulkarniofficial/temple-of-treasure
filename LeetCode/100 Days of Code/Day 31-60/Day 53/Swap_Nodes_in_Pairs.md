# [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

## Solutions

### Solution 1

```
var swapPairs = function(head) {
    let dummy = new ListNode(0, null)
    dummy.next = head
    let fast = dummy.next
    let slow = dummy
    while(fast){
        let temp = fast.next
        if(!temp) return dummy.next
        fast.next = temp.next
        temp.next = fast
        slow.next = temp
        slow = fast
        fast = fast.next
    }
    return dummy.next
};
```

TC: O(n)
SC: O(1)