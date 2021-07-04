# [1220. Count Vowels Permutation](https://leetcode.com/problems/count-vowels-permutation/)

## Solutions

### Solution 1

```
function getNumber(n, c, dp){
    if(dp[n+','+c]) return dp[n+','+c]
    if(n===1) return 1
    let res = null
    if(c==='a'){
        res = getNumber(n-1, 'e', dp)%(Math.pow(10,9)+7)
    }else if(c==='e'){
        res = (getNumber(n-1, 'a', dp) + getNumber(n-1, 'i', dp))%(Math.pow(10,9)+7)
    }else if(c==='i'){
        res = (getNumber(n-1, 'a', dp) + getNumber(n-1, 'e', dp) + getNumber(n-1, 'o', dp) + getNumber(n-1, 'u', dp))%(Math.pow(10,9)+7)
    }else if(c==='o'){
        res = (getNumber(n-1, 'i', dp) + getNumber(n-1, 'u', dp))%(Math.pow(10,9)+7)
    }else if(c==='u'){
        res = (getNumber(n-1, 'a', dp))%(Math.pow(10,9)+7)
    }
    
    dp[n+','+c] = res
    return res
}

var countVowelPermutation = function(n) {
    let dp = {}
    let a = getNumber(n, 'a', dp)
    let e = getNumber(n, 'e', dp)
    let i = getNumber(n, 'i', dp)
    let o = getNumber(n, 'o', dp)
    let u = getNumber(n, 'u', dp)
    return (a+e+i+o+u)%(Math.pow(10,9)+7)
};
```