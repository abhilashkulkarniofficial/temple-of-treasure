# [Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)

Given an undirected graph, return true if and only if it is bipartite.

Recall that a graph is bipartite if we can split its set of nodes into two independent subsets A and B, such that every edge in the graph has one node in A and another node in B.

The graph is given in the following form: graph[i] is a list of indexes j for which the edge between nodes i and j exists. Each node is an integer between 0 and graph.length - 1. There are no self edges or parallel edges: graph[i] does not contain i, and it doesn't contain any element twice.

### Examples

```
Input: graph = [[1,3],[0,2],[1,3],[0,2]]
Output: true
Explanation: We can divide the vertices into two groups: {0, 2} and {1, 3}.

Input: graph = [[1,2,3],[0,2],[0,1,3],[0,2]]
Output: false
Explanation: We cannot find a way to divide the set of nodes into two independent subsets.
```

## My Solution

```
/**
 * @param {number[][]} graph
 * @return {boolean}
 */
let adjMatrix = null
let colorArr = null

function getAdjMatrix(graph){
    adjMatrix = []
    colorArr = []
    let len = graph.length
    for(let i=0; i<len; i++){
        adjMatrix.push([])
        colorArr.push(-1)
        for(let j=0; j<len; j++){
            if(graph[i].includes(j)){
                adjMatrix[i].push(1)
            }else{
                adjMatrix[i].push(0)
            }
        }
    }
}

function isBipartiteUtil(graph,src){
    let queue = []
    queue.unshift(src)
    while(queue.length!=0){
        let u = queue.pop()
        if(adjMatrix[u][u]==1){
            return false
        }
        
        for(let v=0; v<graph.length; v++){
            if(adjMatrix[u][v] === 1 && colorArr[v] === -1){
                colorArr[v] = 1 - colorArr[u]
                queue.unshift(v)
            }else if(adjMatrix[u][v] === 1 && colorArr[v] === colorArr[u]){
                return false
            }
        }
    }
    return true
}

var isBipartite = function(graph) {
    getAdjMatrix(graph)
    console.log(adjMatrix, colorArr)
    for(let i=0; i<graph.length; i++){
        if(colorArr[i] === -1){
            if(!isBipartiteUtil(graph,i)){
                return false
            }
        }
    }
    return true
};
```

[Resource](https://www.geeksforgeeks.org/bipartite-graph/)
