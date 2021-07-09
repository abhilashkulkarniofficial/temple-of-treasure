# [718. Maximum Length of Repeated Subarray](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)

## Solutions

### Solution 1

```
var findLength = function(a, b, maxSoFar = 0) {
    if (a.length === 0 || b.length === 0) {
        return 0
    }

    let n = a.length
    let m = b.length
    
    let dp = new Array(m+1).fill(new Array(n+1).fill(0))
    let max = 0
    
    for(let i=1; i<m+1; i++){
        for(let j=1; j<n+1; j++){
            if(a[i-1]===b[j-1]){
                dp[i][j] = dp[i-1][j-1]+1
            }else{
                dp[i][j] = 0
            }
            max = Math.max.apply(Math,[max, dp[i][j]])
        }
    }
    console.log(dp)
    return max
};
```