# [1474. Delete N Nodes After M Nodes of a Linked List](https://leetcode.com/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/)

## Solutions

### Solution 1

Using fast and slow pointers
```
var deleteNodes = function(head, m, n) {
    let dummy = new ListNode(0, head)
    let fast = dummy
    let slow = dummy
    while(fast){
        if(!fast.next) slow.next = fast.next
        let x = m
        let y = n
        while(fast && slow && x){
            // console.log(fast.val, slow.val)
            fast = fast.next
            slow = slow.next
            x--
        }
        while(fast && fast.next && y){
            // console.log(fast.val)
            fast = fast.next
            y--
        }
        if(slow){
            slow.next = fast.next
        }
        
        // console.log(head)
    }
    return dummy.next
};
```

TC: O(n)
SC: O(1)