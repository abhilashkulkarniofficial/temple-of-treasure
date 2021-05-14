# [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

## Solutions

### Solution 1

```
function createSubtrees(array){
    let parentIndex = parseInt(array.length/2)
    let node = new TreeNode(array[parentIndex], null, null)
    
    // console.log(array.slice(0,parentIndex), array.slice(parentIndex+1,array.length))
    
    if(array.slice(0,parentIndex).length){
        node.left = createSubtrees(array.slice(0,parentIndex))
    }
    
    if(array.slice(parentIndex+1,array.length).length){
        node.right = createSubtrees(array.slice(parentIndex+1,array.length))
    }
    
    // console.log("Node"node)
    
    return node
}

var sortedArrayToBST = function(nums) {
    return createSubtrees(nums)
};
```
