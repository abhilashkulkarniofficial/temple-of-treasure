# [513. Find Bottom Left Tree Value](https://leetcode.com/problems/find-bottom-left-tree-value/)

## Solution

### Solution 1

```
let levelNode = {}

function traverse(node, level){
    if(!node.left && !node.right){
        levelNode[level] = node.val
    }
    
    if(node.right){
        traverse(node.right, level + 1)
    }
    
    if(node.left){
        traverse(node.left, level +1)
    }
    
    return
}

var findBottomLeftValue = function(root) {
    levelNode={}
    traverse(root, 1)
    return levelNode[Math.max.apply(Math, Object.keys(levelNode))]
};
```
