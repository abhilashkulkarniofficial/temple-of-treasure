# [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

## Solutions

### Solution 1

```
function checkSubroot(node, subRoot){
    if(!node && !subRoot) return true
    else if(!node || !subRoot) return false
    
    if(node.val !== subRoot.val) return false
    else{
        let left = checkSubroot(node.left, subRoot.left)
        let right = checkSubroot(node.right, subRoot.right)
        
        return left&&right
    }
    
}

var isSubtree = function(root, subRoot) {
    let hasSubroot = false
    
    let queue = [root]
    
    while(queue.length && !hasSubroot){
        let node = queue.pop()
        if(node.val === subRoot.val) hasSubroot = checkSubroot(node, subRoot)
        if(node.left) queue.unshift(node.left)
        if(node.right) queue.unshift(node.right)
    }
    
    return hasSubroot
};
```