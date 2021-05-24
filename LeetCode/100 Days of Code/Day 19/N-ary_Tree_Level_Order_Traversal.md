# [429. N-ary Tree Level Order Traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)

## Solutions

### Solution 1

BFS approach

```
let list = []

function narybfs(queue){
    if(!queue.length) return
    
    let temp = []
    let len = queue.length
    
    while(len){
        let node = queue.pop()
        temp.push(node.val)
        for(let i=0; i<node.children.length; i++){
            queue.unshift(node.children[i])
        }
        len--
    }
    
    list.push(temp)
    
    narybfs(queue)
    
    return
}

var levelOrder = function(root) {
    if(!root) return []
    list = []
    narybfs([root])
    return list
};
```