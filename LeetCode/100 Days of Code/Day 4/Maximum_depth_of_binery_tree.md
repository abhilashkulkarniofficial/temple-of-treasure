# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

## Solutions

### Solution 1

```
function getMaxLevel(node, finalLevel, level){
    if(!node.left && !node.right){
        list.push(level)
    }
    
    if(node.left){
        getMaxLevel(node.left, list, level+1)
    }
    
    if(node.right){
        getMaxLevel(node.right, list, level+1)
    }
    
    return list
}

var maxDepth = function(root) {
    if(!root) return 0
    let levels = getMaxLevel(root, [], 1)
    return Math.max.apply(Math, levels)
};
```

Optimized solution coming soon.
