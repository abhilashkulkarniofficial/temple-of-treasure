# [Longest Harmonious Subsequence](https://leetcode.com/problems/longest-harmonious-subsequence/)

We define a harmonious array as an array where the difference between its maximum value and its minimum value is exactly 1.

Given an integer array nums, return the length of its longest harmonious subsequence among all its possible subsequences.

A subsequence of array is a sequence that can be derived from the array by deleting some or no elements without changing the order of the remaining elements.

### Examples

```
Input: nums = [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].

Input: nums = [1,2,3,4]
Output: 2

Input: nums = [1,1,1,1]
Output: 0
```

## My tries

```
function allSubsequences(array, index, subarray){
    if(index === array.length){
        // console.log(subarray)
    }else{
        console.log(array[index],subarray)
        allSubsequences(array, index+1, subarray)
        subarray.push(array[index])
        console.log(array[index],subarray)
        allSubsequences(array, index+1, subarray)
    }
    return
}

function iterSubarrays(array){
  let lenArray = []
  for(let i=0;i<array.length;i++){
    for(let j=i; j<array.length;j++){
      let subarray = array.slice(i,j+1)
      if((Math.max.apply(Math,subarray)-Math.min.apply(Math,subarray))===1){
        lenArray.push(subarray.length)
      }
    }
  }
  return Math.max.apply(Math,lenArray)
}

function iterSubsequence(array){
  let size = Math.pow(2, array.length)
  let lenArray = 0
  for(let i=1; i<size; i++){
    let subarray = []
    if((array.length)>lenArray){
      for(let j=0; j<array.length; j++){
      if(i&(1<<j)){
        subarray.push(array[j])
      }
    }
    if((Math.max.apply(Math,subarray)-Math.min.apply(Math,subarray))===1){
        lenArray=subarray.length
      }
    }
    
  }
  return lenArray
  
}

function anotherTry(array){
  let ret = 0
  let obj = {}
  for(let i=0; i<array.length; i++){
    if(obj[array[i]]){
      obj[array[i]]++
    }else{
      obj[array[i]]=1
    }
  }
  let keys = Object.keys(obj)
  for(let i=0; i<keys.length; i++){
    // console.log(obj[parseInt(keys[i])+1])
    if(obj[parseInt(keys[i])+1]!=undefined){
      ret = Math.max.apply(Math,[ret,obj[parseInt(keys[i])]+obj[parseInt(keys[i])+1]])
    }
  }
  return ret
}

var findLHS = function(nums) {
    // allSubsequences(nums, 0, [])
    return anotherTry(nums)
};

findLHS([0,3,1,3,3,3,0,1,0,2,0,3,1,3,-3,2,0,3,1,2,2,-3,2,2,3,3])
```

[Found the algo here for O(n) implementation](https://medium.com/@harshvardhansingh_67029/longest-harmonious-subsequence-a9933b6c78dd)

[Generating all possible Subsequences using Recursion](https://www.geeksforgeeks.org/generating-all-possible-subsequences-using-recursion/)
