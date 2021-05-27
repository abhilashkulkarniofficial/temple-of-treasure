# [720. Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)

## Solutions

### Solution 1

```
let word = ""

function TrieNode(val, children, terminates, length){
    this.val = val
    this.children = children
    this.terminates = terminates
    this.length = length
}

var Trie = function(){
    this.root = new TrieNode("root", new Array(26), false, 0)
}

Trie.prototype.insert = function(word){
    let curr = this.root
    let i=0
    while(i<word.length){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]) curr.children[c.charCodeAt() - 'a'.charCodeAt()] = new TrieNode(c, new Array(26), false, 0)
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
        i++
    }
    curr.terminates = true
    curr.length = i
    // console.log(curr)
}

function lonely(node){
    let children = node.children
    for(let i=0; i<children.length; i++){
        if(children[i]) return false
    }
    return true
}

var findLongestWord = function(node, str){
    if(lonely(node)){
        if(word.length < str.length){
            word = str
        }
        return false
    }
    
    let children = node.children
    let signal = false
    let child = null
    for(let i=0; i<children.length; i++){
        child = children[i]
        if(child && child.terminates){
            signal = findLongestWord(child, str+child.val)
        }
    }
    if(word.length < str.length){
        word = str
    }
    return
}

var longestWord = function(words) {
    word = ""
    let trie = new Trie()
    for(let i=0; i<words.length; i++){
        trie.insert(words[i])
    }
    findLongestWord(trie.root, "")
    return word
};
```