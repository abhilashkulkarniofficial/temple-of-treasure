# [106. Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

## Solutions

### Solution 1

```
function subtree(io, po){
    let parent = po[po.length -1]
    let node = new TreeNode(parent, null, null)
    
    let nodeIndex = io.indexOf(parent)
    let leftstart = 0
    let leftend = nodeIndex
    let rightstart = nodeIndex
    let rightend = po.length - 1
    
    if(io.slice(leftstart, leftend).length){
        node.left = subtree(io.slice(leftstart, leftend), po.slice(leftstart, leftend))
    }
    
    if(io.slice(nodeIndex+1,rightend+1).length){
    node.right = subtree(io.slice(nodeIndex+1,rightend+1),po.slice(nodeIndex,rightend))
    }
    
    
    return node
}

var buildTree = function(inorder, postorder) {
    return subtree(inorder, postorder)
};
```
