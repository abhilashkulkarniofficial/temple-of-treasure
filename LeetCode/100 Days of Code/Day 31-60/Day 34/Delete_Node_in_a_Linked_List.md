# [237. Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)

## Solutions

### Solution 1

```
var deleteNode = function(node) {
    node.val = node.next.val
    node.next = node.next.next
};
```

TC: O(1)
SC: O(1)