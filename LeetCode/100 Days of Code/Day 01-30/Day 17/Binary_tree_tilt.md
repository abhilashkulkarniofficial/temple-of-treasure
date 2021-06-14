# [563. Binary Tree Tilt](https://leetcode.com/problems/binary-tree-tilt/)

## Solutions

### Solution 1

This approach is crude but works fast.

```
function traverse(node, tilt, sum){    
    if(!node.left && !node.right){
        if(tilt){
            let val = node.val
            node.val = 0
            sum+=node.val
            return [node, val, sum]
        }else{
            return [node, node.val, sum]
        }
    }
    
    let [leftnode, leftval] = [null, 0]
    let [rightnode, rightval] = [null, 0]
    if(node.left){
        [leftnode, leftval, sum] = traverse(node.left, tilt, sum)
    }
    
    if(node.right){
        [rightnode, rightval, sum] = traverse(node.right, tilt, sum)
    }
    
    if(tilt){
        let val = node.val
        node.val = Math.abs(leftval-rightval)
        sum+=node.val
        return [node, val, sum]
    }else{
        node.val = leftval+rightval+node.val
        return [node, node.val, sum]
    }
    
}

var findTilt = function(root) {
    if(!root) return 0
    let [node,val, sum] = traverse(root, false, 0)
    let nodes = traverse(node, true, 0)
    return nodes[2]
};

```