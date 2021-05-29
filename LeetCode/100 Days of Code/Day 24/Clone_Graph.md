# [133. Clone Graph](https://leetcode.com/problems/clone-graph/)

## Solutions

### Solution 1

```
function clone(node, visited){
    let queue = [node]
    let newNode = new Node(node.val, [])
    let q2 = [newNode]
    let nodeObj = {}
    nodeObj[newNode.val] = newNode
    visited[node.val] = true
    while(queue.length){
        let c = queue.pop()
        
        let c2 = q2.pop()
        // console.log(c.val, c2.val)
        for(const x of c.neighbors){
            if(!visited[x.val]){
                visited[x.val] = true
                let n = new Node(x.val, [])
                q2.unshift(n)
                nodeObj[n.val] = n
                c2.neighbors.push(n)
                queue.unshift(x)
            }else{
                c2.neighbors.push(nodeObj[x.val])
            }
        }
    }
    return newNode
}

var cloneGraph = function(node) {
    if(node === null) return
    let visited = {}
    return clone(node, visited)
};
```