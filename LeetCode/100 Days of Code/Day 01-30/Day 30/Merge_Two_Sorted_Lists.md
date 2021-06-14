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

### Solution 2

```
var mergeTwoLists = function(l1, l2) {
    let dummy = new ListNode(0,null)
    let d2 = dummy
    while(l1 && l2){
        if(l1.val < l2.val){
            let node = new ListNode(l1.val, null)
            d2.next = node
            d2 = node
            l1 = l1.next
        }else{
            let node = new ListNode(l2.val, null)
            d2.next = node
            d2 = node
            l2 = l2.next
        }
    }
    
    while(l1){
        let node = new ListNode(l1.val, null)
        d2.next = node
        d2 = node
        l1 = l1.next
    }
    
    while(l2){
        let node = new ListNode(l2.val, null)
        d2.next = node
        d2 = node
        l2 = l2.next
    }
    return dummy.next
};
```

TC: O(n1+n2)
SC: O(n1+n2)

### Solution 3

Inplace solution.
Step 1: point n1 to the smaller node and n2 to bigger node
Step 2: point res to n1
Iteration: 
    - point temp to null, while n1 is less than n2, point temp to n1 and n1 to next of n1
    - if n1 > n2, point temp to n2 and swap n1 and n2
    - do this till either one points to null
Return res

```
var mergeTwoLists = function(l1, l2) {
    if(!l1) return l2
    if(!l2) return l1
    let n1 = l1.val<=l2.val?l1:l2
    let n2 = l1.val>l2.val?l1:l2
    let res = n1
    while(n1 && n2){
        let temp = null
        while(n1 && n2 && n1.val<=n2.val){
            temp = n1
            n1 = n1.next
        }
        temp.next = n2
        let x = n1
        n1 = n2
        n2 = x
    }
    return res
};
```

TC: O(n1+n2)
SC: O(1)