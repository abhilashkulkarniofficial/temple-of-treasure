# [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

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
    
    list.push(temp)
    
    bfs(queue)
    
    return
}

var levelOrder = function(root) {
    if(!root) return []
    list = []
    let queue = [root]
    bfs(queue)
    return list
};
```