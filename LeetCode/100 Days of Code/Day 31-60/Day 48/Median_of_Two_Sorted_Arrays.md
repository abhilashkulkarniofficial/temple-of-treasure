# [4. Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)

## Solutions

### Solution 1

```
var findMedianSortedArrays = function(nums1, nums2) {
    // Approach 1
    let i=0
    let j=0
    let mergedArr = []
    while(i<nums1.length || j<nums2.length){
        if(i<nums1.length && j<nums2.length){
            if(nums1[i]<nums2[j]) {
                mergedArr.push(nums1[i])
                i++
            }else{
                mergedArr.push(nums2[j])
                j++
            }
        }else if(i<nums1.length){
            mergedArr.push(nums1[i])
            i++
        }else{
            mergedArr.push(nums2[j])
            j++
        }
    }
    // console.log(mergedArr,i,j)
    if((i+j)%2){
        return mergedArr[parseInt((i+j)/2)]
    }else{
        return (mergedArr[parseInt((i+j-1)/2)]+mergedArr[parseInt((i+j)/2)])/2
    }
};
```

TC: O(n+m)
SC: O(n+m)