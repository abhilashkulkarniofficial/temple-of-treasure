# [559. Maximum Depth of N-ary Tree](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)

## Solution

### Solution 1

```
function getHeight(node){
        
    let arr = []
        
    
    for(let i=0; i<node.children.length; i++){
        // console.log(node.children[i])
        arr.push(getHeight(node.children[i]))
    }
    
    
    if(!node.children.length){
        return 1
    }else{
        return 1 + Math.max.apply(Math, arr)
    }
    
}

var maxDepth = function(root) {
    if(!root) return 0
    return getHeight(root)
};
```
