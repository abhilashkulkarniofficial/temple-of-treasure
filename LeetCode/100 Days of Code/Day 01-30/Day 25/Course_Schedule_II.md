# [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)

## Solutions

### Solution 1

```
function topologicalSort(list, incoming, n){
    let finalList = []
    let node = 1
    while(n && node!==undefined){
        node = undefined
        let i = 0
        while(i<incoming.length && node === undefined){
            if(incoming[i]===0) node = i
            i++
        }
        if(node!==undefined){
            let neighbors = list[node]
            finalList.push(node)
            for(let j=0; j<neighbors.length; j++){
                incoming[neighbors[j]]--
            }
            incoming[node] = undefined
        }
        
        n--
    }
    return finalList
    
}

function createAdjList(prereq, n){
    let list = new Array(n)
    let incoming = new Array(n)
    
    for(let i=0; i<prereq.length; i++){
        let p = prereq[i]
        if(!list[p[1]]) {
            list[p[1]] = []
        }
        
        if(incoming[p[0]]===undefined){
           incoming[p[0]] = 0
        }
        list[p[1]].push(p[0])
        incoming[p[0]]++
        // console.log(incoming[p[0]])
    }
    
    for(let i=0; i<n; i++){
        if(!list[i]) list[i] = []
        if(incoming[i]===undefined) incoming[i] = 0
    }
    
    return [list, incoming]
}


var findOrder = function(numCourses, prerequisites) {
    let [list, incoming] = createAdjList(prerequisites, numCourses)
    let finallist = topologicalSort(list, incoming, numCourses)
    return finallist.length===numCourses?finallist:[]
};
```