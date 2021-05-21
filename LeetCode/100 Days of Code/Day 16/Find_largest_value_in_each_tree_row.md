# [515. Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)

## Solutions

### Solution 1

```
let largest = {}

function traverse(node, level){
    if(!node) return
    
    if(largest[level]===undefined) largest[level] = node.val
    else if(largest[level] < node.val) {
        largest[level] = node.val
    }
    
    traverse(node.left, level+1)
    traverse(node.right, level+1)
    
    return
    
}

var largestValues = function(root) {
    largest = {}
    traverse(root, 0)
    return Object.values(largest)
};
```