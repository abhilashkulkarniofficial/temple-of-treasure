# [872. Leaf-Similar Trees](https://leetcode.com/problems/leaf-similar-trees/)

## Solution

### Solution 1

Approach:
Traverse the tree and push all leaf nodes to a list. Compare the two list.

```
function traverse(node, list){
    if(!node.left && !node.right){
        list.push(node.val)
        return list
    }
    
    if(node.left) traverse(node.left, list)
    if(node.right) traverse(node.right, list)
    
    return list
}

var leafSimilar = function(root1, root2) {
    let list1 = traverse(root1, [])
    let list2 = traverse(root2, [])
    return list1.length === list2.length &&
        list1.every(function(value, index){
        return value === list2[index]
    })
};
```
