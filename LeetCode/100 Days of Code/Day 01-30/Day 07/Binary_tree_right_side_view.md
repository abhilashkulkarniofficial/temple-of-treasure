# [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

## Solutions

### Solution 1

Approach using DFS and global object to store the rightmost node.

```
let levelNodes = {}

function traverse(node, level){
    if(!node){
        return 
    }
    
    traverse(node.left, level+1)
    traverse(node.right, level+1)
    
    levelNodes[level] = node.val
    
    return 
}

var rightSideView = function(root) {
    levelNodes = {}
    traverse(root, 1)
    return Object.values(levelNodes)
};
```
