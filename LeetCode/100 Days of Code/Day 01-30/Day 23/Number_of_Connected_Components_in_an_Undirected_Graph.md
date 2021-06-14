# [323. Number of Connected Components in an Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)

## Solutions

### Solution 1

```
function traverse(list, visited, i){
    let queue = []
    queue.push(i)
    while(queue.length){
        let x = queue.pop()
        let nodes = list[x]
        visited[x] = true
        for(let j=0; j<nodes.length; j++){
            if(!visited[nodes[j]]){
                queue.push(nodes[j])
            }
        }
    }
    return visited
}

function createAdjacencyList(n, edges){
    let adlist = new Array(5)
    for(let i=0; i<edges.length; i++){
        let node1 = edges[i][0]
        let node2 = edges[i][1]
        if(!adlist[node1]) {
            adlist[node1] = [node2]
        }else{
            adlist[node1].push(node2)
        }
        if(!adlist[node2]) {
            adlist[node2] = [node1]
        }else{
            adlist[node2].push(node1)
        }
    }
    return adlist
    
}

var countComponents = function(n, edges) {
    let count = 0
    let adlist = createAdjacencyList(n, edges)
    let visited = {}
    for(let i=0; i<n; i++){
        visited[i] = false
        if(!adlist[i]) adlist[i] = []
    }
    console.log(adlist)
    for(let i=0; i<n; i++){
        if(!visited[i]){
            visited = traverse(adlist, visited, i)
            console.log(visited)
            count++
        }
        
    }
     return count                                
};
```