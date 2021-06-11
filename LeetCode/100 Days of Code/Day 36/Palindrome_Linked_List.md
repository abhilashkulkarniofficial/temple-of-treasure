# [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

## Solutions

### Solution 1

```
var isPalindrome = function(head) {
    let arr = []
    while(head){
        arr.push(head.val)
        head = head.next
    }
    let i=0
    let j=arr.length-1
    while(i<j){
        if(arr[i]!==arr[j]) return false
        i++
        j--
    }
    return true
    
};
```

TC: O(2n)
SC: O(n)

### Solution 2

```
var isPalindrome = function(head) {
    let dummy = new ListNode(0, head)
    let s = dummy
    let f = dummy
    while(f && f.next){
        s = s.next
        f = f.next.next
    }
    let x = s.next
    let d = null
    while(x){
        let temp = x.next
        x.next = d
        d = x
        x = temp
    }
    s.next = d
    s = s.next
    d = head
    while(s){
        if(s.val !== d.val) return false
        s = s.next
        d = d.next
    }
    return true
};
```

TC: O(3n/2) = O(n)
SC: O(1)