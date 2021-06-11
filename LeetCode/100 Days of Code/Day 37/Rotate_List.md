# [61. Rotate List](https://leetcode.com/problems/rotate-list/)

## Solutions

### Solution 1

```
var rotateRight = function(head, k) {
    if(!head || !head.next || !k) return head
    let dummy = new ListNode(0, head)
    let slow = dummy
    let fast = dummy
    let len = 0
    let curr = head
    while(curr){
        len++
        curr = curr.next
    }
    if(k%len===0) return head
    else k = k%len +1
    while(fast){
        fast = fast.next
        if(k){
            k--
        }else{
            slow = slow.next
        }
    }
    let x = slow.next
    let beg = x
    slow.next = null
    while(x.next){
        x = x.next
    }
    x.next = head
    return beg
};
```

TC: O(n+n-k%n)
SC: O(1)

### Solution 2

Cleaner approach

```
var rotateRight = function(head, k) {
    if(!head || !head.next) return head
    let len = 1
    let node = head
    while(node.next){
        len++
        node = node.next
    }
    node.next = head
    let dis = len - k%len
    console.log(len,k,dis)
    while(dis){
        node = node.next
            dis--
    }
    head = node.next
    node.next = null
    return head
};
```

TC: O(n+n-k%n)
SC: O(1)