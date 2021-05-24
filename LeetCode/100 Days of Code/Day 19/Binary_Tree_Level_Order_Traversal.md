# [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

## Solutions

### Solution 1

```
function inorderTraversal(node, list){
    if(!node) return list
    
    inorderTraversal(node.left, list)
    list.push(node.val)
    inorderTraversal(node.right, list)
    
    return list
}

var kthSmallest = function(root, k) {
    let list = inorderTraversal(root, [])
    return list[k-1]
};
```