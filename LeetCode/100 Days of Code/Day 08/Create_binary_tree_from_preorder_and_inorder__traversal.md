# [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

## Solution

### Solution 1

```
function subtree(io, po){
    let parent = po[0]
    let node = new TreeNode(parent, null, null)
    
    let nodeIndex = io.indexOf(parent)
    let leftstart = 0
    let leftend = nodeIndex
    let rightstart = nodeIndex + 1
    let rightend = po.lengtht
    
    if(io.slice(leftstart, leftend).length){
        node.left = subtree(io.slice(leftstart, leftend), po.slice(leftstart+1, nodeIndex+1))
    }
    
    if(io.slice(nodeIndex+1,rightend+1).length){
    node.right = subtree(io.slice(nodeIndex+1,rightend),po.slice(nodeIndex+1,rightend))
    }
    
    
    return node
}

var buildTree = function(preorder, inorder) {
    return subtree(inorder, preorder)
};
```
