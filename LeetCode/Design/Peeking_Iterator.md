# [Peeking Iterator](https://leetcode.com/problems/peeking-iterator/)

Given an Iterator class interface with methods: next() and hasNext(), design and implement a PeekingIterator that support the peek() operation -- it essentially peek() at the element that will be returned by the next call to next().

### Example:

```
Assume that the iterator is initialized to the beginning of the list: [1,2,3].

Call next() gets you 1, the first element in the list.
Now you call peek() and it returns 2, the next element. Calling next() after that still return 2. 
You call next() the final time and it returns 3, the last element. 
Calling hasNext() after that should return false.
```

## Operator

```
/**
 * // This is the Iterator's API interface.
 * // You should not implement it, or speculate about its implementation.
 * function Iterator() {
 *    @ return {number}
 *    this.next = function() { // return the next number of the iterator
 *       ...
 *    }; 
 *
 *    @return {boolean}
 *    this.hasNext = function() { // return true if it still has numbers
 *       ...
 *    };
 * };
 */

/**
 * @param {Iterator} iterator
 */
let peekedElement = null
let hasPeeked = false

var PeekingIterator = function(iterator) {
    this.iterator = iterator
};

/**
 * @return {number}
 */
PeekingIterator.prototype.peek = function() {
    if(!hasPeeked){
        peekedElement = this.iterator.next()
        hasPeeked = true
    }
    return peekedElement
};

/**
 * @return {number}
 */
PeekingIterator.prototype.next = function() {
    if(!hasPeeked){
        return this.iterator.next()
    }
    let result = peekedElement
    hasPeeked = false
    peekedElement = null
    return result
};

/**
 * @return {boolean}
 */
PeekingIterator.prototype.hasNext = function() {
    return hasPeeked || this.iterator.hasNext()
};

/** 
 * Your PeekingIterator object will be instantiated and called as such:
 * var obj = new PeekingIterator(arr)
 * var param_1 = obj.peek()
 * var param_2 = obj.next()
 * var param_3 = obj.hasNext()
 */
```

[Google's Guava Peeking Iterator](https://github.com/google/guava/blob/703ef758b8621cfbab16814f01ddcc5324bdea33/guava-gwt/src-super/com/google/common/collect/super/com/google/common/collect/Iterators.java#L1125)
