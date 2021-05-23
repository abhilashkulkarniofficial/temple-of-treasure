# [993. Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/)

## Solutions

### Solution 1

This problem is BFS but this is a DFS approach.

```
let left = []
let right = []

function traverse(node, x, y, level, parent){
    // console.log(parent)
    if(!node) return
    if(!parent) parent = new TreeNode(0, null)
    
    if(node.val === x){
        left = [level+1, parent.val]
    }else if(node.val === y){
        right = [level+1, parent.val]
    }
    
    
    traverse(node.left, x, y, level+1, node)
    traverse(node.right, x, y, level+1, node)
    
    return
    
}

var isCousins = function(root, x, y) {
    left = []
    right = []
    traverse(root, x, y, 0, null)
    return left[0]===right[0]&&left[1]!==right[1]
};
```