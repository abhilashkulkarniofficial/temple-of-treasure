# [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

## Solutions

### Solution 1

```
function invertedTree(node){
    if(!node) return null
    
    let newNode = new TreeNode(node.val, null, null)
    
    newNode.left = invertedTree(node.right)
    newNode.right = invertedTree(node.left)
    
    return newNode
}

var invertTree = function(root) {
    return invertedTree(root)
};
```