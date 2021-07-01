# [1325. Delete Leaves With a Given Value](https://leetcode.com/problems/delete-leaves-with-a-given-value/)

## Solutions

### Solution 1

```
var removeLeafNodes = function(root, target) {
    if(!root) return root
    
    if(!root.left && !root.right && root.val === target) return null
    root.left = removeLeafNodes(root.left, target)
    root.right = removeLeafNodes(root.right, target)
    if(!root.left && !root.right && root.val === target) return null
    return root
};
```

TC: O(n)
SC: O(1)