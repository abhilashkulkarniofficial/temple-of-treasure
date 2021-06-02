# [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

## Solutions

### Solution 1

```
var deleteDuplicates = function(head) {
    if(!head) return null
    let newNode = new ListNode(head.val, null)
    let curr = newNode
    let arr = [head.val]
    head = head.next
    while(head){
        if(!arr.includes(head.val)){
            let node = new ListNode(head.val, null)
            curr.next = node
            curr = node
            arr.push(head.val)
        }
        head = head.next
    }
    return newNode
};
```