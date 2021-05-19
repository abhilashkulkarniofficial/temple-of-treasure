# [1448. Count Good Nodes in Binary Tree](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)

## Solution

### Solution 1

```
let numberOfGoodNodes = 0

function checkGreater(list){
    let last = list.pop()
    return list.every((value, index) => {return value <= last})
}

function traverse(node, list){
    if(!node) return
    
    list.push(node.val)
    
    if(checkGreater([...list])){
        numberOfGoodNodes ++
    }
    
    traverse(node.left, list)
    traverse(node.right, list)
    
    list.pop()
    
    return
}

var goodNodes = function(root) {
    numberOfGoodNodes = 0
    traverse(root, [])
    return numberOfGoodNodes
};
```