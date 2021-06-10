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