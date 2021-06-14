# [733. Flood Fill](https://leetcode.com/problems/flood-fill/)

## Solutions

### Solution 1

This is a very crude approach using graph DFS

```
function dfs(image, sr, sc, newColor, visited, prevColor){
    if(image[sr][sc] === prevColor){
        image[sr][sc] = newColor
    }
    let left = [sr,Math.max.apply(Math,[sc-1,0])]
    let top = [Math.max.apply(Math,[sr-1,0]),sc]
    let right = [sr,Math.min.apply(Math,[sc+1,image[0].length-1])]
    let bottom = [Math.min.apply(Math,[sr+1,image.length-1]),sc]

    if(!visited.includes(left[0]+''+left[1]) && image[left[0]][left[1]] === prevColor){
        visited.push(left[0]+''+left[1])
        dfs(image, left[0], left[1], newColor, visited, prevColor)
    }
    if(!visited.includes(right[0]+''+right[1]) && image[right[0]][right[1]] === prevColor){
        visited.push(right[0]+''+right[1])
        dfs(image, right[0], right[1], newColor, visited, prevColor)
    }
    if(!visited.includes(top[0]+''+top[1])&& image[top[0]][top[1]] === prevColor){
        visited.push(top[0]+''+top[1])
        dfs(image, top[0], top[1], newColor, visited, prevColor)
    }
    if(!visited.includes(bottom[0]+''+bottom[1])&& image[bottom[0]][bottom[1]] === prevColor){
        visited.push(bottom[0]+''+bottom[1])
        dfs(image, bottom[0], bottom[1], newColor, visited, prevColor)
    }
    return
}

var floodFill = function(image, sr, sc, newColor) {
    let visited = [sr+''+sc]
    let prevColor = image[sr][sc]
    dfs(image, sr, sc, newColor, visited, prevColor)
    return image
};
```