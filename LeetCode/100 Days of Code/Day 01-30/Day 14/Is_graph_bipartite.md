# [785. Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)

## Solutions

### Solution 1

This approach uses DFS to check if the graph is bipartite. Not very efficient as it uses coloring method. 

```
let visited = {}
let setA = []
let setB = []

function checkBipartite(node, graph, set){
    visited[node] = true
    let nodes = graph[node]
    // console.log(visited, setA, setB, set)
    
    for(let i=0; i<nodes.length; i++){
        if(set && !setB.includes(nodes[i])){
            setB.push(nodes[i])
        }else if(!set && !setA.includes(nodes[i])){
            setA.push(nodes[i])
        }
    }
    
    for(let i=0; i<graph[node].length; i++){
        if(!visited[nodes[i]]){
            checkBipartite(nodes[i], graph, !set)
        }
    }
    
    return 
}

var isBipartite = function(graph) {
    visited = {}
    for(let i=0; i<graph.length; i++){
        visited[i] = false
    }
    setA = []
    setB = []
    for(let i=0; i<graph.length; i++){
        if(!visited[i]){
            setA.push(i)
            checkBipartite(i, graph, true)
            console.log(i, visited, setA, setB)
        }
    }
    for(let i=0; i<setA.length; i++){
        if(setB.includes(setA[i])) return false
    }
    return true
};
```

