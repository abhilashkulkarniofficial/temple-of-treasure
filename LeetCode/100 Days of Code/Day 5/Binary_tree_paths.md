# [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)

## Solutions

### Solution 1

Bottom up approach:

```
function traverse(node){
    if(!node.left && !node.right){
        return ["" + node.val]
    }
    
    let list = []
    
    if(node.left){
        let strList = traverse(node.left)
        for(let i=0; i<strList.length; i++){
            list.push(node.val + "->" + strList[i])
        }
    } 
    
    if(node.right){
        let strList = traverse(node.right)
        for(let i=0; i<strList.length; i++){
            list.push(node.val + "->" + strList[i])
        }
    } 
    
    return list
    
}

var binaryTreePaths = function(root) {
    return traverse(root)
};
```

### Solution 2

Top Down approach

```
let paths = []

function traverse(node, path){
    if(!node.left && !node.right){
        return paths.push(path + node.val)
    }
    
    path = path + node.val + "->"
        
    if(node.left){
        traverse(node.left, path)
    } 
    
    if(node.right){
        traverse(node.right, path)
    } 
    
}

var binaryTreePaths = function(root) {
    traverse(root, "")
    console.log(paths)
    return paths
};

```

