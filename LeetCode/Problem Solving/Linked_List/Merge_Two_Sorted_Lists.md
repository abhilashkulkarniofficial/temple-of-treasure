# Merge Two Sorted Lists

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

### My initial solution

```
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
 
// Input: l1 = [1,2,4], l2 = [1,3,4]
// Output: [1,1,2,3,4,4]

// Input: l1 = [], l2 = []
// Output: []

// Input: l1 = [], l2 = [0]
// Output: [0]
 
var mergeTwoLists = function(l1, l2) {
    if(l1=='undefined' || l1==null) return l2
    else if(l2 == 'undefined' || l2==null) return l1
    let mergedList = null
    let tail = null
    let nodel1 = l1
    let nodel2 = l2
    while(nodel1!=null && nodel2!=null){
        let node = null
        if(nodel1.val <= nodel2.val){
            node = new ListNode(nodel1.val, null)
            // console.log(node)
            nodel1 = nodel1.next
        }else{
            node = new ListNode(nodel2.val, null)
            // console.log(node)
            nodel2 = nodel2.next
            
        }
        
        if(mergedList == null) {
            mergedList = node
            tail = node
        }
        else{
            tail.next = node
            tail = node
        } 
    }
    
    let finalnode = null
    if(nodel1 == null){
        finalnode = nodel2
    }else{
        finalnode = nodel1
    }
    
    while(finalnode!=null){
        node = new ListNode(finalnode.val, null)
        
        tail.next = node
        tail = node
        
        finalnode = finalnode.next
    }
    
    return mergedList
    
};
```
