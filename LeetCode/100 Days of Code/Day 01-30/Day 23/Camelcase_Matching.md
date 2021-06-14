# [1023. Camelcase Matching](https://leetcode.com/problems/camelcase-matching/)

## Solutions

### Solution 1

```
let list = {}

function TrieNode(val){
    this.val = val
    this.children = new Array(52)
    this.terminates = false
}

var Trie = function(){
    this.root = new TrieNode("root")
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

Trie.prototype.insert = function(word){
    let curr = this.root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        let index = getIndex(c)
        if(!curr.children[index]) curr.children[index] = new TrieNode(c)
        curr = curr.children[index]
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

function matching(node, pattern, index, str){
    // console.log(node.val, pattern, index)
    if(node.terminates){
        if(index === pattern.length) {
            list[str] = true
            console.log(str,true)
        }
    }
    
    let children = node.children
    for(let i=0; i<children.length; i++){
        let child = children[i]
        if(child){
            if(child.val === pattern[index]){
                matching(child, pattern, index+1, str+child.val)
            }else if(getIndex(child.val) < 26){
                matching(child, pattern, index, str+child.val)
            }
        }
    }
    return 
}

var camelMatch = function(queries, pattern) {
    list = {}
    let trie = new Trie()
    for(let i=0; i<queries.length; i++){
        list[queries[i]] = false
        trie.insert(queries[i])
    }
    matching(trie.root, pattern, 0, "")
    return Object.values(list)
};
```