# [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

### Examples

```
Input: [1,2,3,null,5,null,4]
Output: [1, 3, 4]
Explanation:

   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
```

## My solution

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
 * @return {number[]}
 */
let right = null


function height(node){
    if(node==null){
        return 0
    }else{
        let height1 = height(node.left)
        let height2 = height(node.right)
        
        if(height1 > height2){
            return height1+=1
        }else{
            return height2+=1
        }
    }
}

function rightmost(node, level){
    if(node==null) return
    if(level == 1) {
        console.log(node.val)
        right = node.val
    }else if(level > 1){
        rightmost(node.left, level -1)
        rightmost(node.right, level-1)
    }
}

var rightSideView = function(root) {
    let treeHeight = height(root)
    let retArray = []
    for(let i=1;i<=treeHeight;i++){
        console.log("Height: "+i)
        rightmost(root, i)
        retArray.push(right)
    }
    return retArray
};
```
