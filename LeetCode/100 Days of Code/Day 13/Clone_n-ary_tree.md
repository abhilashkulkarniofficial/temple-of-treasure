# [1490. Clone N-ary Tree](https://leetcode.com/problems/clone-n-ary-tree/)

## Solutions

### Solution 1

```
var cloneTree = function(root) {
    if(!root) return null
    let node = new Node(root.val, null)
    
    let rootChildren = root.children
    let newChildren = []
    for(let i=0; i<rootChildren.length; i++){
        newChildren.push(cloneTree(rootChildren[i]))
        // console.log(rootChildren[i])
    }
    
    node.children = newChildren
    
    return node
};
```