# [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

## Solutions

### Solution 1

```
var getIntersectionNode = function(headA, headB) {
    let d1 = headA
    let d2 = headB
    while(true){
        if(d1===d2) return d1
        d1 = d1.next
        d2 = d2.next
        if(!d1 && !d2) return d1
        if(!d1) d1 = headB
        if(!d2) d2 = headA
    }
};
```

TC: O(2M)
SC: O(1)