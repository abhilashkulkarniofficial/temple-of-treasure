# [1602. Find Nearest Right Node in Binary Tree](https://leetcode.com/problems/find-nearest-right-node-in-binary-tree/)

## Solutions

### Solution 1

```
function getRightNode(queue,target){
    if(!queue.length) return
    
    let len = queue.length
    
    while(len){
        let node = queue.pop()
        if(node===target){
            if(len===1) return null
            return queue.pop()
        }
        if(node.left) queue.unshift(node.left)
        if(node.right) queue.unshift(node.right)
        
        len--
    }
    
    let node = getRightNode(queue, target)
    
    return node
}

var findNearestRightNode = function(root, u) {
    return getRightNode([root],u)
};
```