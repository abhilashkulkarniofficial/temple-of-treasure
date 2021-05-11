# [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)

## Solutions

### Solution 1

```
function traverse(node, list, low, high){
    if(!node) return
    
    if(node.val >= low && node.val <= high){
        list.push(node.val)
    }
    
    traverse(node.left, list, low, high)
    traverse(node.right, list, low, high)
    
    return list
    
}

var rangeSumBST = function(root, low, high) {
    let list = traverse(root, [], low, high)
    return list.reduce((a,b) => {return a+b})
};
```
