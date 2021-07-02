# [82. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

## Solutions

### Solution 1

```
var deleteDuplicates = function(head) {
    if(!head) return head
    let hash = {}
    let arr = []
    let node = head
    while(node){
        if(!hash[node.val]) hash[node.val] = 1
        else hash[node.val]++
        arr.push(node.val)
        node = node.next
    }
    console.log(hash)
    let dummy = new ListNode(0, null)
    node = dummy
    
    for(let i=0; i<arr.length; i++){
        if(hash[arr[i]]===1){
            let newNode = new ListNode(arr[i],null)
            node.next = newNode
            node = node.next
        }
    }
    return dummy.next
};
```

TC: O(2n)
SC: O(2n)

### Solution 2

```
var deleteDuplicates = function(head) {
    if(!head) return head
    let dummy = new ListNode(0, null)
    dummy.next = head
    let slow = dummy
    let fast = dummy.next
    while(fast){
        let temp = fast
        fast = fast.next
        while(fast && fast.val===temp.val){
            fast = fast.next
        }
        if(temp.next === fast && (!fast || fast.val!==temp.val)){
            slow.next = temp
            slow = temp
        }else if(temp.next && !fast){
            slow.next = fast
        }
        
    }
    if(slow===dummy) return null
    return dummy.next
};
```

TC: O(n)
SC: O(1)