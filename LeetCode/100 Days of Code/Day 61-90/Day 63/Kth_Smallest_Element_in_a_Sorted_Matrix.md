# [378. Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

## Solutions

### Solution 1

```
function myCount(i, matrix){
    let n = matrix.length
    let row = 0
    let col = n-1
    let count = 0
    while(row<n && col>=0){
        if(matrix[row][col]<=i){
            count+=col+1
            row++
        }else{
            col--
        }
    }
    return count
}

var kthSmallest = function(matrix, k) {
    let n = matrix.length
    let matrix_min = matrix[0][0]
    let matrix_max = matrix[n-1][n-1]
    
    while(matrix_min < matrix_max){
        let mid = parseInt((matrix_min+matrix_max)/2)
        if(myCount(mid, matrix)<k){
            matrix_min = mid+1
        }else{
            matrix_max = mid
        }
    }
    return matrix_max
};
```