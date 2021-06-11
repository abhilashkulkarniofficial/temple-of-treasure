# [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

## Solutions

### Solution 1

```
var detectCycle = function(head) {
    let nodearr = []
    let node = head
    while(node){
        if(nodearr.includes(node)) return node
        nodearr.push(node)
        node = node.next
    }
    return null
};
```

TC: O(n)
SC: O(n)

### Solution 2

Using fast and slow pointers

```
var detectCycle = function(head) {
    if(!head) return null
    let dummy = new ListNode(0,head)
    let s = dummy
    let f = dummy
    while(true){
        s = s.next
        f = f.next.next
        if(!f || !f.next) return null
        if(s===f) break
    }
    let d = dummy
    while(true){
        s = s.next
        d = d.next
        if(s===d) return d
    }
};
```

TC: O(n)
SC: O(1)