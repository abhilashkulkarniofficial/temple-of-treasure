# [Trim a Binary Search Tree](https://leetcode.com/problems/trim-a-binary-search-tree/)

Given the root of a binary search tree and the lowest and highest boundaries as low and high, trim the tree so that all its elements lies in [low, high]. Trimming the tree should not change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a unique answer.

### Examples

```
Input: root = [1,0,2], low = 1, high = 2
Output: [1,null,2]

Input: root = [3,0,4,null,2,null,null,1], low = 1, high = 3
Output: [3,2,null,1]

Input: root = [1], low = 1, high = 2
Output: [1]

Input: root = [1,null,2], low = 1, high = 3
Output: [1,null,2]

Input: root = [1,null,2], low = 2, high = 4
Output: [2]
```

## My implementation

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
 * @param {number} low
 * @param {number} high
 * @return {TreeNode}
 */
let count = 0

function remove(root, val){
    let parent = null
    let node = root
    while(node){
        if(val < node.val){
            parent = node
            node = node.left
        }else if(val > node.val){
            parent = node
            node = node.right
        }else if(val == node.val){
            // console.log(node)
            if(node.right === null){
                if(parent === null) root = node.left
                else{
                    if(node.val < parent.val) {
                        parent.left = node.left
                    }
                    else if(node.val > parent.val) {
                        parent.right = node.left
                    }
                }
            } else if (node.left === null) {
                if(parent === null) root = node.right
                else{
                    if(node.val < parent.val) {
                        parent.left = node.right
                    }
                    else if(node.val > parent.val) {
                        parent.right = node.right
                    }
                }
            } else {
                if(node.right.left === null){
                    node.right.left = node.left
                    if(parent === null) root = node.right
                    else{
                        if(node.val < parent.val) parent.left = node.right
                        else if(node.val > parent.val) parent.right = node.right
                    }
                }
            }
            // console.log(root)
            return root
        }
    }
    
    
}

function traverse(root, node, low, high){
    if(!node) return
    traverse(root, node.left, low, high)
    traverse(root, node.right, low, high)
    if(node.val < low || node.val > high) {
        // console.log(node.val)
        count++
        root = remove(root, node.val)
    }
    return root
    
}


var trimBST = function(root, low, high) {
    root = traverse(root, root, low, high)
    console.log(count)
    return root
};
```

## Need to work on a better solution
