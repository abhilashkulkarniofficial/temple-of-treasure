# [1469. Find All The Lonely Nodes](https://leetcode.com/problems/find-all-the-lonely-nodes/)

## Solutions

### Solution 1

Approach:
1. Do a preorder DFS. 
2. Check if the parent has only 1 child, then push node.val. 
3. Check if node has left child, traverse left.
4. Check if node has right child, traverse right.

```
function traverse(parent, node, list){    
    if(parent && !(parent.left && parent.right)){
        list.push(node.val)
    }
    
    if(node.left){
        traverse(node, node.left, list)
    }
    
    if(node.right){
        traverse(node, node.right, list)
    }
    
    return list
}

var getLonelyNodes = function(root) {
    let list = traverse(null, root, [])
    console.log(list)
    
    return list
};
```
