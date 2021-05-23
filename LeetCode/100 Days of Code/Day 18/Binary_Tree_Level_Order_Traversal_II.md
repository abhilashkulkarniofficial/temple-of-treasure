# [107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

## Solutions

### Solution 1

BFS approach

```
let list = []

function bfs(queue){
    if(!queue.length) return
    
    let temp = []
    let len = queue.length
    
    while(len){
        let node = queue.pop()
        temp.push(node.val)
        if(node.left) queue.unshift(node.left)
        if(node.right) queue.unshift(node.right)
        len--
    }
    
    bfs(queue)
    
    list.push(temp)
    
    return
    
}

var levelOrderBottom = function(root) {
    if(!root) return []
    list = []
    bfs([root])
    return list
};
```