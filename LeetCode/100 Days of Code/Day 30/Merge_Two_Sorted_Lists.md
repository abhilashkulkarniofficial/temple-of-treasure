# [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

## Solutions

### Solution 1

```
var mergeTwoLists = function(l1, l2) {
    let arr = []
    while(l1 || l2){
        if(!l1) {
            arr.push(l2.val)
            l2 = l2.next
        }else if(!l2){ 
            arr.push(l1.val)
            l1 = l1.next
        }
        else{
            if(l1.val < l2.val){
                arr.push(l1.val)
                l1 = l1.next
            }else{
                arr.push(l2.val)
                l2 = l2.next
            }
        }
    }
    
    let head = null
    if(!arr.length) return head
    head = new ListNode(arr[0], null)
    let curr = head
    for(let i=1; i<arr.length; i++){
        let newNode = new ListNode(arr[i], null)
        curr.next = newNode
        curr = newNode
    }
   return head
    
    
};
```