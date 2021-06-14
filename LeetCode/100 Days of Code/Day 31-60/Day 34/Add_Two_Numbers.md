# [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

## Solutions

### Solution 1

```
var addTwoNumbers = function(l1, l2) {
    // Brute approach
    let dummy = new ListNode(0, null)
    let temp = dummy
    let sum = 0
    let carry = 0
    while(l1 || l2){
        sum = carry
        if(l1){
            sum = sum + l1.val
            l1 = l1.next
        }
        if(l2){
            sum = sum + l2.val
            l2 = l2.next
        }
        carry = parseInt(sum/10)
        let newNode = new ListNode(sum%10, null)
        temp.next = newNode
        temp = newNode
    }
    if(carry){
        let newNode = new ListNode(carry, null)
        temp.next = newNode
    }
    return dummy.next
};
```

TC: O(max(m,n))
SC: O(N)