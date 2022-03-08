
```


function lower_bound (array, target, low = 0, high = array.length - 1) {
  if (low > high) {
    return -1
  }
  const midPoint = Math.floor((low + high) / 2)

  if (target < array[midPoint]) {
    return lower_bound(array, target, low, midPoint - 1)
  } else if (target > array[midPoint]) {
    return lower_bound(array, target, midPoint + 1, high)
  } else {
    return array[midPoint]
  }
}

var maxSumSubmatrix = function(matrix, k) {
    let n = matrix.length;
    let m = matrix[0].length
    let ans = Number.MIN_VALUE
    for(let i=0; i<n; i++){
        for(let j=1; j<m; j++){
            matrix[i][j]+=matrix[i][j-1]
        }
    }
    
    for(let start=0; start<m; start++){
        for(let end = start; end<m; end++){
            let s = new Set()
            let pref_sum = 0
            
            for(let i=0; i<n; i++){
                let sum = matrix[i][end]
                if(start>0) sum-=matrix[i][start-1]
                pref_sum+=sum
                let lower = lower_bound([...s], pref_sum-k)
                console.log(pref_sum-k, lower, s)
                if(lower!==-1) ans = Math.max.apply(Math, [ans, pref_sum-lower])
                s.add(pref_sum)
            }
        }
    }
    return ans
    
};
```