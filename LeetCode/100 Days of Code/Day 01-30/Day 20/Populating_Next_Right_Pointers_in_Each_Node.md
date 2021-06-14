# [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

## Solutions

### Solution 1

```
function populateNextPointer(queue){
    if(!queue.length) return
    
    let len = queue.length
    let temp = []
    
    while(len){
        let node = queue.pop()
        temp.push(node)
        if(node.left) queue.unshift(node.left)
        if(node.right) queue.unshift(node.right)
        len--
    }
    
    for(let i=0; i<temp.length-1; i++){
        temp[i].next = temp[i+1]
    }
    
    console.log(temp)
    
    populateNextPointer(queue)
    return
}

var connect = function(root) {
    if(!root) return root
     populateNextPointer([root])
    return root
```