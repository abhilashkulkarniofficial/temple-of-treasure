# [25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)

## Solutions

### Solution 1

```
var reverseKGroup = function(head, k) {
    let dummy = new ListNode(0, head)
    let n1 = dummy
    let n2 = dummy
    let len = 0
    let x = head
    while(x){
        len++
        x = x.next
    }
    let itr = parseInt(len/k)
    while(n1 && n2 && itr){
        let d = null
        let i = k
        n1 = n1.next
        while(i){
            if(!n1) return dummy.next
            let temp = n1.next
            n1.next = d
            d = n1
            n1 = temp
            i--
        }
        itr--
        let temp = n2.next
        n2.next.next = n1
        n2.next = d
        n2  = temp
        n1 = temp        
        
    }
    return dummy.next
};
```

TC: O(2n)
SC: O(1)

### Solution 2

```
var reverseKGroup = function(head, k) {
    let dummy = new ListNode(0,head)
    let pre = dummy
    let count = 0
    let node = head
    while(node){
        count++
        node = node.next
    }
    while(count>=k){
        let curr = pre.next
        let nex = curr.next
        let i = k-1
        while(i){
            curr.next = nex.next
            nex.next = pre.next
            pre.next = nex
            nex = curr.next
            i--
        }
        count = count-k
        pre = curr
    }
    return dummy.next
};
```

TC: O(n/k)*k = O(n)
SC: (1)