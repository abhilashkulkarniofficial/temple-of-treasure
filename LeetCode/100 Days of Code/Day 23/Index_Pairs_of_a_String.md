# [1065. Index Pairs of a String](https://leetcode.com/problems/index-pairs-of-a-string/)

## Solutions

### Solution 1

```
let list = []

function TrieNode(val){
    this.val = val
    this.children = new Array(26)
    this.terminates = false
}

var Trie = function(){
    this.root = new TrieNode("root")
}

Trie.prototype.insert = function(word){
    let curr = this.root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]) curr.children[c.charCodeAt() - 'a'.charCodeAt()] = new TrieNode(c)
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    curr.terminates = true
}

function getIndex(char){
    if(char.charCodeAt() < 97){
        return char.charCodeAt() - 'A'.charCodeAt() + 26
    }else{
        return char.charCodeAt() - 'a'.charCodeAt()
    }
}

function traverse(node, str){
    if(node.terminates){
        console.log(str)
    }
    
    let children = node.children
    for(let i=0; i<children.length; i++){
        let child = children[i]
        if(child){
            traverse(child, str+child.val)
        }
    }
    return 
}



function lonely(node){
    let children = node.children
    for(let i=0; i<children.length; i++){
        if(children[i]) return false
    }
    return true
}

function checker(node, text, startIndex, index){
    if(node.terminates){
        list.push([startIndex, index -1])
        if(lonely(node)){
            return
        }
    }
    
    if(index < text.length){
        let c = text[index]
        let child = node.children[c.charCodeAt() - 'a'.charCodeAt()]
        if(child){
            checker(child, text, startIndex, index+1)
        }
    }
    return
}

var indexPairs = function(text, words) {
    list = []
    let trie = new Trie()
    for(let i=0; i<words.length; i++){
        trie.insert(words[i])
    }
    // traverse(trie.root,"")
    let children = trie.root.children
    for(let i=0; i<text.length; i++){
        let c = text[i]
        let child = children[c.charCodeAt() - 'a'.charCodeAt()]
        if(child){
            checker(child, text, i, i+1)
        }
    }
    return list
};
```