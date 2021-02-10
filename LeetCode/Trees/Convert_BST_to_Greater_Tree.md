# [Convert BST to Greater Tree](https://leetcode.com/problems/convert-bst-to-greater-tree/)

Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

As a reminder, a binary search tree is a tree that satisfies these constraints:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
Note: This question is the same as 1038: https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/

### Examples

```
Input: root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
Output: [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]

Input: root = [0,null,1]
Output: [1,null,1]

Input: root = [1,0,2]
Output: [3,3,2]

Input: root = [3,2,4,1]
Output: [7,9,4,10]
```

## My Solution

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {TreeNode}
 */
function traverse(root, sum){
    if(!root){
        return root
    }else{
        traverse(root.right, sum)
        sum[0] = sum[0] + root.val
        root.val = sum[0]
        traverse(root.left, sum)
    }
    
}

var convertBST = function(root) {
    let sum = [0]
    traverse(root, sum)
    return root
};
```

