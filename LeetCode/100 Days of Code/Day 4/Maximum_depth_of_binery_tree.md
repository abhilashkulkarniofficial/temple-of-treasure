# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

## Solutions

### Solution 1

```
function getMaxLevel(node, list, level){
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

### Solution 2

Better looking approach. Uses more memory though.

```
function getMaxLevel(node){
    if(!node.left && !node.right){
        return 1
    }
    
    let maxLevel = 0
    
    if(node.left){
        maxLevel = Math.max.apply(Math, [getMaxLevel(node.left), maxLevel])
    }
    
    if(node.right){
        maxLevel = Math.max.apply(Math, [getMaxLevel(node.right), maxLevel])
    }
    
    return maxLevel + 1
}

var maxDepth = function(root) {
    if(!root) return 0
    return getMaxLevel(root)
};
```
