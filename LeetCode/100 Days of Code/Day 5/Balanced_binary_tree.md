# [110. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

## Solutions

### Solution 1

Very crude solution. Approach is based on checking if the right subtree and the left subtree are balanced at every level.

```
function traverse(node){
    if(!node){
        return [true, 1]
    }
    
    let left = [true, 0]
    let right = [true, 0]
    
    left = traverse(node.left)
    right = traverse(node.right)

//     console.log(node, left, right)
    
    return [
        Math.abs(left[1] - right[1]) < 2 && left[0] && right[0],
        Math.max.apply(Math, [left[1], right[1]]) + 1
           ]
}

var isBalanced = function(root) {
    if(!root) return true
    let heightLeft = traverse(root.left)
    let heightRight = traverse(root.right)
    // console.log(heightLeft, heightRight)
    return Math.abs(heightLeft[1] - heightRight[1]) <= 1 && heightLeft[0] && heightRight[0]
};
```

Working on a optimized solution.
