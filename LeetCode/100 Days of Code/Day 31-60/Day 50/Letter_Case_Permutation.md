# [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)

## Solutions

### Solution 1

```
function combination(index, s, list, str){
    if(index===s.length){
        list.push(str)
        return
    }
    
    combination(index+1, s, list, str+s[index])
    if(s[index]>='a' && s[index]<='z'){
        let x = s[index].toUpperCase()
        combination(index+1, s, list, str+x)
    }else if(s[index]>='A' && s[index]<='Z'){
        let x = s[index].toLowerCase()
        combination(index+1, s, list, str+x)
    }
    return
}

var letterCasePermutation = function(s) {
    let list = []
    combination(0, s.toLowerCase(), list,'')
    return list
};
```