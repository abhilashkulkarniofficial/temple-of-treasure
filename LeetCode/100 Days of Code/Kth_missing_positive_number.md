# (1539. Kth Missing Positive Number)[https://leetcode.com/problems/kth-missing-positive-number/]

### Accepted Solution

'''
var findKthPositive = function(arr, k) {
    let i = 0
    while(k > 0){
        // console.log(num, i, k)
        i++
        if(i >= arr[arr.length-1]){
            i+=k
            k=0
        }else if(!arr.includes(i)){
            k--
        }
    }
    return i
};
'''
