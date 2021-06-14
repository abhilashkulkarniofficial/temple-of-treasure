# [783. Minimum Distance Between BST Nodes](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

## Solutions

### Solution 1

Crude approach to solving this.

```
function preorderTraverse(node, list){
    list.push(node.val)
    
    if(node.left){
        preorderTraverse(node.left, list)
    }
    
    if(node.right){
        preorderTraverse(node.right, list)
    }
    
    
    return list
}

var minDiffInBST = function(root) {
    let list = preorderTraverse(root, [])
    
    let minDifference = Infinity
    
    for(let i=0; i<list.length-1; i++){
        for(let j=1; j<list.length; j++){
            let diff = Math.abs(list[j]-list[i])
            if(diff<minDifference && i!==j){
                minDifference = diff
            }
        }
    }
    
    return minDifference
    
};
```

Time complexity is high because of the comparisons. Need a better way to compare. 

Also why isn't the travesal giving a list in preorder? Need to check on this.
