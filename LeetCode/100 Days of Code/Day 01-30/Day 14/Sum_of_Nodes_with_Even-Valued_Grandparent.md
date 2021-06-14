# [1315. Sum of Nodes with Even-Valued Grandparent](https://leetcode.com/problems/sum-of-nodes-with-even-valued-grandparent/)

## Solution

### Solution 1

```
function traverse(parent, grandparent, node, sum){
    if(!node) return sum
    
    if(grandparent && grandparent.val%2===0){
        sum+=node.val
    }
    
    sum = traverse(node, parent, node.left, sum)
    
    sum = traverse(node, parent, node.right, sum)
    
    return sum
    
}

var sumEvenGrandparent = function(root) {
    return traverse(null, null, root, 0)
};
```