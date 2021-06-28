# [328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)

## Solutions

### Solution 1

```
var oddEvenList = function(head) {
    if(!head || !head.next){
        return head
    }
    let oddStart = head
    let evenStart = head.next
    let odd = oddStart
    let even = oddStart.next
    while(even && even.next){
        // console.log(dummy.next)
        let slow = even.next
        let fast = slow.next
        odd.next = slow
        slow.next = evenStart
        odd = slow
        even.next = fast
        even = even.next
        // console.log(odd,even)
    }
    return oddStart
};
```

TC: O(n)
SC: O(1)