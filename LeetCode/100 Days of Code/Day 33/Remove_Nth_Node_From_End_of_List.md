# [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

## Solutions

### Solution 1

```
var removeNthFromEnd = function(head, n) {
    if(head.next === null){
        if(n===1){
            return null
        }
    }
    let arr = []
    let node = head
    while(node!=null){
        arr.push(node.val)
        node = node.next
    }
    arr.splice(arr.length - n, 1)
    node = head
    for(let i=0; i<arr.length - 1; i++){
        node.val = arr[i]
        node = node.next
    }
    node.val = arr[arr.length-1]
    node.next = null
    return head
};
```