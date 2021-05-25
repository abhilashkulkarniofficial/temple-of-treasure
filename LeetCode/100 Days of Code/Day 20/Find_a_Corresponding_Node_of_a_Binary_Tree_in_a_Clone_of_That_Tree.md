# [1379. Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)

## Solutions

### Solution 1

BFS approach

```
var getTargetCopy = function(original, cloned, target) {
    let queue1 = [original]
    let queue2 = [cloned]
    
    while(queue1.length){
        let node1 = queue1.pop()
        let node2 = queue2.pop()
        // console.log(node1.val, node2.val)
        if(node1 === target){
            return node2
        }
        if(node1.left){
            queue1.unshift(node1.left)
            queue2.unshift(node2.left)
        }
        
        if(node1.right){
            queue1.unshift(node1.right)
            queue2.unshift(node2.right)
        }
    }
    
    return
};
```

### Solution 2

DFS approach. DFS performs faster than BFS

```
var getTargetCopy = function(original, cloned, target) {
    if(!original) return
    
    if(original === target) return cloned
    
    let node1 = getTargetCopy(original.left, cloned.left, target)
    
    let node2 = getTargetCopy(original.right, cloned.right, target)
    
    if(node1) return node1
    return node2
};
```