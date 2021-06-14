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

### Solution 2

Inplace removal

```
var removeNthFromEnd = function(head, n) {
    if(!head.next && n===1){
        return null
    }
    let len = 0
    let node = head
    while(node){
        node = node.next
        len++
    }
    let dummy = head
    let pos = len - (n+1)
    if(n===len){
        head = head.next
    }else{
        while(pos){
            dummy = dummy.next
            pos--
        }
        if(dummy.next){
            dummy.next = dummy.next.next
        }else{
            dummy.next = null
        }
    }
    
    // console.log(dummy)
    
    return head
    
};
```

TC: O(n) + O(n)
SC: O(1)

### Solution 3

Using 2 pointers

```
var removeNthFromEnd = function(head, n) {
    if(!head.next && n===1){
        return null
    }
    let dummy = new ListNode(0, head)
    let fast = dummy
    let slow = dummy
    n++
    while(fast){
        if(n){
            fast = fast.next
            n--
        }else{
            fast = fast.next
            slow = slow.next
        }
    }
    slow.next = slow.next.next
    return dummy.next
    
};
```

TC: O(n)
SC: O(1)