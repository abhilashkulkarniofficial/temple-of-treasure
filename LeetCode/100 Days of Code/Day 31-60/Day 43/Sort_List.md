# [148. Sort List](https://leetcode.com/problems/sort-list/)

## Solutions

### Solution 1

```
var sortList = function(head) {
    if(!head) return head
    let arr = []
    let node = head
    while(node){
        arr.push(node.val)
        node = node.next
    }
    arr.sort(function(a,b){return a-b})
    node = head
    let i=0
    while(node){
        node.val = arr[i]
        node = node.next
        i++
    }
    return head
};
```

TC: O(n)+O(n)+O(nlogn)
SC: O(n)