# [1302. Deepest Leaves Sum](https://leetcode.com/problems/deepest-leaves-sum/)

## Solutions

### Solution 1

Using global variable and checking height of the tree.

```
let sum = 0

function getHeight(node){
    if(!node) return 0
    
    return 1 + Math.max.apply(Math, [
        getHeight(node.left), getHeight(node.right)
    ])
}

function getDeepestLeavesSum(node, level, height){
    if(level===height && !node.left && !node.right){
        sum += node.val
        return
    }
    
    if(node.left){
        getDeepestLeavesSum(node.left, level+1, height)
    }
    
    if(node.right){
        getDeepestLeavesSum(node.right, level+1, height)
    }
    
}

var deepestLeavesSum = function(root) {
    sum = 0
    let height = getHeight(root)
    getDeepestLeavesSum(root, 1, height)
    return sum
};
```

Need a better approach to solving this.
