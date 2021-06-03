# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

## Solutions

### Solution 1

```
var removeElements = function(head, val) {
    if(!head) return head
    let node = head
    let arr = []
    while(node){
        if(node.val!==val){
            arr.push(node.val)
        }
        node=node.next
    }
    if(!arr.length) return null
    let newNode = new ListNode(arr[0], null)
    let i=1
    node = newNode
    while(i<arr.length){
        let temp = new ListNode(arr[i], null)
        node.next = temp
        node = node.next
        i++
    }
    return newNode
};
```