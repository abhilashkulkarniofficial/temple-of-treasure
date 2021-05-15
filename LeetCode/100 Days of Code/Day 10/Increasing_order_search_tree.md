# [897. Increasing Order Search Tree](https://leetcode.com/problems/increasing-order-search-tree/)

## Solutions

### Solution 1

```
function inorderTraversal(node, list){
    if(!node) return
    
    inorderTraversal(node.left, list)
    
    list.push(node.val)
    
    inorderTraversal(node.right, list)
    
    return list
}

function createInorderSearchTree(inorder){
    let node = new TreeNode(inorder[0], null, null)
    
    let restOfTheTree = inorder.slice(1,inorder.length)
    
    if(restOfTheTree.length){
        node.right = createInorderSearchTree(restOfTheTree)
    }
    
    return node
}

var increasingBST = function(root) {
    let inorder = inorderTraversal(root, [])
    return createInorderSearchTree(inorder)
};
```
