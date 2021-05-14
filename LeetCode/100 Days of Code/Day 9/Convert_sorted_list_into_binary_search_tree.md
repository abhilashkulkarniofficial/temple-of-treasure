# [109. Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

## Solutions

### Solution 1

Approach:
1. Convert the list into an array.
2. Create BST using the array.

```
function listToArray(node){
    let arr = []
    while(node){
        arr.push(node.val)
        node = node.next
    }
    
    return arr
}

function createSubtrees(array){
    let parentIndex = parseInt(array.length/2)
    let node = new TreeNode(array[parentIndex], null, null)
    
    if(array.slice(0,parentIndex).length){
        node.left = createSubtrees(array.slice(0,parentIndex))
    }
    
    if(array.slice(parentIndex+1,array.length).length){
        node.right = createSubtrees(array.slice(parentIndex+1,array.length))
    }
    
    // console.log("Node"node)
    
    return node
}

var sortedListToBST = function(head) {
    if(!head){
        return head
    }
    return createSubtrees(listToArray(head))
};
```
