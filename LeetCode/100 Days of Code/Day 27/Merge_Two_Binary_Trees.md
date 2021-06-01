# [617. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)

## Solutions

### Solution 1

```
function traverse(node1, node2){
    if(!node1 && !node2){
        return null
    }
        
    let newNode = new TreeNode(0, null, null)
    let left1 = undefined
    let left2 = undefined
    let right1 = undefined
    let right2 = undefined
    if(node1){
        newNode.val+=node1.val
        left1 = node1.left
        right1 = node1.right
    }
    
    if(node2){
        newNode.val+=node2.val
        left2 = node2.left
        right2 = node2.right
    }
    
    newNode.left = traverse(left1, left2)
    newNode.right = traverse(right1, right2)
    
    return newNode
}

var mergeTrees = function(root1, root2) {
    return traverse(root1, root2)
};
```