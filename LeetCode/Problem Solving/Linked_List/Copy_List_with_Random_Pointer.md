# [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.

Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. None of the pointers in the new list should point to nodes in the original list.

For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> y.

Return the head of the copied linked list.

The linked list is represented in the input/output as a list of n nodes. Each node is represented as a pair of [val, random_index] where:

val: an integer representing Node.val
random_index: the index of the node (range from 0 to n-1) that the random pointer points to, or null if it does not point to any node.
Your code will only be given the head of the original linked list.

### Examples

```
Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]

Input: head = [[1,1],[2,1]]
Output: [[1,1],[2,1]]

Input: head = [[3,null],[3,0],[3,null]]
Output: [[3,null],[3,0],[3,null]]

Input: head = []
Output: []
Explanation: The given linked list is empty (null pointer), so return null.
```

## My solution

```
/**
 * // Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

/**
 * @param {Node} head
 * @return {Node}
 */
function copyNodes(head){
    let p = head
    while(p){
        let copy = new Node(p.val, null, null)
        copy.next = p.next
        p.next = copy
        p = copy.next
    }
    
    p = head
    while(p){
        if(p.random){
            p.next.random = p.random.next
        }
        p = p.next.next
    }
    
    p = head
    let newHead = head.next
    while(p){
        let temp = p.next
        p.next = temp.next
        if(temp.next){
            temp.next = temp.next.next
        }
        p = p.next
    }
    return newHead
}

var copyRandomList = function(head) {
    if(!head) return null
    let newHead = copyNodes(head)
    console.log(newHead)
    return newHead
};
```

[Implementation explanation](https://www.programcreek.com/2012/12/leetcode-copy-list-with-random-pointer/)
