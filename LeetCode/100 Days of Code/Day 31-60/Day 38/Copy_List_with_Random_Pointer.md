# [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

## Solutions

### Solution 1

```
var copyRandomList = function(head) {
    let iter = head
    let front = head
    while(iter){
        front = iter.next
        let copy = new Node(iter.val, null, null)
        iter.next = copy
        copy.next = front
        iter = front
    }
    
    iter = head
    while(iter){
        if(iter.random) iter.next.random = iter.random.next
        iter = iter.next.next
    }
    
    iter = head
    let dummy = new Node(0,null, null)
    let copy = dummy
    while(iter){
        let front = iter.next.next
        copy.next = iter.next
        iter.next = front
        copy = copy.next
        iter = iter.next
    }
    return dummy.next
};
```

TC: O(n) + O(n) + O(n)
SC: O(1)