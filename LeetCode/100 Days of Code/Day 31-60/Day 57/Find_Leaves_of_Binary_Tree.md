# [366. Find Leaves of Binary Tree](https://leetcode.com/problems/find-leaves-of-binary-tree/)

## Solutions

### Solution 1

```
function dfs(node, list){
    if(!node.left && !node.right){
        list.push(node.val)
        return null
    }else if(node){
        if(node.left) node.left = dfs(node.left, list)
        if(node.right) node.right = dfs(node.right, list)
    }

    return node
}

var findLeaves = function(root) {
    let masterList = []
    while(root){
        let list = []
        if(!root.left && !root.right) {
            list.push(root.val)
            root = null
        }else{
            dfs(root, list)
        }
        
        masterList.push(list)
    }
    
    return masterList
};
```

TC: O(nlogn)
SC: O(1)