# [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

## Solutions

### Solution 1

```
let digitDictionary = {'2':['a','b','c'], '3':['d','e','f'], '4':['g','h','i'], '5':['j','k','l'], 6':['m','n','o'], '7':['p','q','r','s'], '8':['t','u','v'], '9':['w','x','y','z']}

let list = []

function letterCombo(index, digits, x){
    if(index===digits.length){
        list.push(x.join(''))
        return
    }
    
    let letters = digitDictionary[digits[index]]
    for(let i=0; i<letters.length; i++){
        x.push(letters[i])
        letterCombo(index+1, digits, x)
        x.pop()
    }
    
    return
}

var letterCombinations = function(digits) {
    list = []
    digits = digits.split('')
    if(!digits.length) return []
    letterCombo(0, digits, [])
    return list
    
};
```