# [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

## Solution

### Solution 1

```
let mainlist = []

function traverse(node, list){
    if(!node.left && !node.right){
        list.push(node.val)
        mainlist.push(list.reduce(function(a,b){return a+''+b}))
        list.pop()
        return
    }
    
    list.push(node.val)
    
    if(node.left) traverse(node.left, list)
    
    if(node.right) traverse(node.right, list)
    
    list.pop()
    
    return 
}

var sumNumbers = function(root) {
    mainlist = []
    traverse(root, [])
    return mainlist.reduce(function(a,b){return parseInt(a)+parseInt(b)})
};
```