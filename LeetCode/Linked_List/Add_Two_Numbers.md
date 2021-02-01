# [Add two numbers](https://leetcode.com/problems/add-two-numbers/)

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Examples
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Input: l1 = [0], l2 = [0]
Output: [0]

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

## My first solution

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
var addTwoNumbers = function(l1, l2) {
    // Brute approach
    let sumList = new ListNode(0, null)
    let tempNode = sumList
    while(l1!=null || l2!=null){
        let sum = tempNode.val
        if(l1==null){ 
            sum+=l2.val
            l2 = l2.next
        }
        else if(l2==null) {
            sum+=l1.val
            l1 = l1.next
        }
        else {
            sum+= l1.val+l2.val
            l2 = l2.next
            l1 = l1.next
        }
        let carry = parseInt(sum/10)
        let digit = sum%10
        tempNode.val = digit
        if(l1==null && l2==null && carry==0){
            tempNode.next = null
        }else{
            tempNode.next = new ListNode(carry, null)
            tempNode = tempNode.next
        }
    }
    
    return sumList
};
```
