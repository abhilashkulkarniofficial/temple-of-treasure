# [261. Graph Valid Tree](https://leetcode.com/problems/graph-valid-tree/)

## Solutions

### Solution 1

```
function bfsTraverse(node, visited, adlist, treeList){
    let queue = [node]
    treeList['0'] = "root"
    
    while(queue.length){
        let c = queue.pop()
        visited[c] = true
        // console.log(c)
        let nodes = adlist[c]
        for(const n of nodes){
            // console.log(n, treeList[n])
            if(treeList[n]!==undefined) return false
            if(!visited[n]) {
                treeList[n] = c
                queue.unshift(n)
                adlist[n].splice(adlist[n].indexOf(c),1)
                // console.log(adlist)
            }
        }
    }
    
    console.log(treeList)
    return true
}

function createAdjacencyList(n, edges){
    let adlist = new Array(n)
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
    
    let visited = {}
    for(let i=0; i<n; i++){
        if(!adlist[i]) adlist[i] = []
        visited[i] = false
    }
    
    return [adlist, visited]
}

var validTree = function(n, edges) {
    let [adlist, visited] = createAdjacencyList(n, edges)
    let treeList = {}
    console.log(adlist, visited)
    return bfsTraverse(0, visited, adlist, treeList) && Object.keys(treeList).length === n
};
```