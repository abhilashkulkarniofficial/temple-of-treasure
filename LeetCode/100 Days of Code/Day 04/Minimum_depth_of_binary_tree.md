# [111. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

## Solutions

### Solution 1

Approach:
1. Using DFS to traverse the tree.
2. Check if a node is a leaf node, push the level into the list.
3. If node has left child and next level is smaller than the minimum level in list, traverse left child.
4. If node has right child and next level is smaller than the minimum level in list, traverse right child.
5. Return list

```
function getAllLevels(node, list, level){
    if(!node.left && !node.right){
        list.push(level)
    }
    
    minLevel = Math.min.apply(Math, list)
    
    if(node.left && (minLevel > level +1)){
        getAllLevels(node.left, list, level +1)
    }
    
    if(node.right && (minLevel > level +1)){
        getAllLevels(node.right, list, level +1)
    }
    
    return list
}

var minDepth = function(root) {
    if(!root) return 0
    let levelList = getAllLevels(root, [], 1)
    console.log(levelList)
    return Math.min.apply(Math, levelList);
};
```

### Solution 2

Better approach without using list:

```
function getAllLevels(node){
    if(!node.left && !node.right){
        return 1
    }
    
    let minLevel = 9999
    
    if(node.left){
        minLevel = Math.min.apply(Math, [minLevel, getAllLevels(node.left)])
    }
    
    if(node.right){
        minLevel = Math.min.apply(Math, [minLevel, getAllLevels(node.right)])
    }
    
    return minLevel + 1
}

var minDepth = function(root) {
    if(!root) return 0
    return getAllLevels(root)
};
```
