# [112. Path Sum](https://leetcode.com/problems/path-sum/)

## Solutions

### Solution 1

Approach:
1. Perform a preorder DFS with a sum.
2. If node is leaf, push sum + node.val into the list.
3. If node has left child, traverse left child with sum = sum + node.val.
4. If node has right child, traverse right child with sum = sum + node.val.
5. Return list
6. Check if the list as target sum.

```
function traverse(node, list, sum){
    if(!node.left && !node.right){
        list.push(sum + node.val)
    }
    
    if(node.left){
        traverse(node.left, list, sum + node.val)
    }
    
    if(node.right){
        traverse(node.right, list, sum + node.val)
    }
    
    return list
}

var hasPathSum = function(root, targetSum) {
    if(!root) return 0
    let sumList = traverse(root, [], 0)
    return sumList.includes(targetSum)
};
```
