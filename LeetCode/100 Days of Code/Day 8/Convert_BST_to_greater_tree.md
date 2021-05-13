# [538. Convert BST to Greater Tree](https://leetcode.com/problems/convert-bst-to-greater-tree/)

## Solutions

### Solution 1

Best solution. Awesome example of Inorder traversal

```
function convertToGreaterBST(node, sum){
    if(!node.left && !node.right){
        node.val += sum
        sum = node.val
        return sum
    }
    
    if(node.right){
        sum = convertToGreaterBST(node.right, sum)
    }
    
    node.val += sum
    sum = node.val
    
    if(node.left){
        sum = convertToGreaterBST(node.left, sum)
    }
    
    return sum
}

var convertBST = function(root) {
    if(!root){
        return root
    }
    convertToGreaterBST(root, 0)
    return root
};
```
