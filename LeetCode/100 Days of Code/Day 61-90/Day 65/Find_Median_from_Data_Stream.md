# [295. Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

## Solutions

### Solution 1

```
/**
 * initialize your data structure here.
 */
var MedianFinder = function() {
    this.array = []
    this.length = 0
};

/** 
 * @param {number} num
 * @return {void}
 */
MedianFinder.prototype.addNum = function(num) {
    this.array.push(num)
    this.array.sort(function(a,b){return a-b})
    this.length++
};

/**
 * @return {number}
 */
MedianFinder.prototype.findMedian = function() {
    if(this.length%2) return this.array[parseInt(this.length/2)]
    else return (this.array[parseInt(this.length/2)-1]+this.array[parseInt(this.length/2)])/2
};

/** 
 * Your MedianFinder object will be instantiated and called as such:
 * var obj = new MedianFinder()
 * obj.addNum(num)
 * var param_2 = obj.findMedian()
 */
```