# [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

## Solutions

### Solution 1

```
var reverseList = function(head) {
    let dummy = null
    while(head){
        let next = head.next
        head.next = dummy
        dummy = head
        head = next
    }
    return dummy
};
```

Time complexity : O(n)
Space complexity : O(1)