# [113. Path Sum II](https://leetcode.com/problems/path-sum-ii/)

## Solutions

### Solution 1

Crude solution using a global list.

```
let lists = []

function getAllPathSums(node, list, sum, targetSum){
    if(!node.left && !node.right){
        if(sum + node.val === targetSum){
            list.push(node.val)
            console.log(node.val, list)
            lists.push([...list])
            list.pop()
        }
        return list
    }
    
    list.push(node.val)
    sum += node.val
    
    if(node.left){
        list = getAllPathSums(node.left, list, sum, targetSum)
    }
    
    if(node.right){
        list = getAllPathSums(node.right, list, sum, targetSum)
    }
    
    list.pop()
    return list
}

var pathSum = function(root, targetSum) {
    lists = []
    if(!root) return lists
    getAllPathSums(root, [], 0, targetSum)
    return lists
};
```
