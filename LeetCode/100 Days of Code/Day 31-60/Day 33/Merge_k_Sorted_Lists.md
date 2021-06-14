# [23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

## Solutions

### Solution 1

```
var mergeKLists = function(lists) {
    if(!lists.length) return null
    let arr = []
    for(var x of lists){
        if(x){
            while(x){
                arr.push(x.val)
                x = x.next
            }
        }
    }
    arr.sort(function(a,b){return a-b})
    let res = new ListNode(arr[0], null)
    let node = res
    for(let i=1; i<arr.length; i++){
        let newNode = new ListNode(arr[i], null)
        node.next = newNode
        node = node.next
    }
    return arr.length?res:null
};
```

TC: O(k*n) where k is number of lists and n is size of lists
SC: O(k*n)