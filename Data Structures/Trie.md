# Trie

### Trie Node
```
var TrieNode = function(val, children, terminates){
    this.val = val
    this.children = children
    this.terminates = terminates
    this.count = 0
}
```

### Trie Initializations
```
var Trie = function() {
    this.root = new TrieNode("root",new Array(26), false)
};
```

### Helper Functions
```
function getnode(word, root){
    let curr = root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]) return null
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    return curr
}

function countAllWords(node){
    if(!node.children.length) return node.count
    let children = node.children
    let count = 0
    for(let i=0; i<children.length; i++){
        if(children[i]){
            count+=countAllWords(children[i])
        }
    }
    return count+node.count
}
```

### Insert
```
Trie.prototype.insert = function(word) {
    let current = this.root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(current.children[c.charCodeAt() - 'a'.charCodeAt()]===undefined){
            current.children[c.charCodeAt() - 'a'.charCodeAt()] = new TrieNode(c,new Array(26), false)
        }
        current = current.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    current.terminates = true
    current.count++
};
```

### Search
```
Trie.prototype.search = function(word) {
    let node = getnode(word, this.root)
    return node !== null && node.terminates
};
```

### StartsWith
```
Trie.prototype.startsWith = function(prefix) {
    return getnode(prefix, this.root) !== null
};
```

### CountWordsEqualTo
```
Trie.prototype.countWordsEqualTo = function(word) {
    let node = getnode(word, this.root)
    return node!==null?node.count:0
};
```

### CountWordsStartingWith
```
Trie.prototype.countWordsStartingWith = function(prefix) {
    let node = getnode(prefix, this.root)
    return node!==null?countAllWords(node):null
};
```

### Traverse
```
function traverse(node, str){
    if(node.terminates){
        console.log(str, node.count)
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
```

### Erase
```
function erase(node, word, index){
    if(index==word.length){
        node.count = node.count -1
        if(node.count) return false
        else{
            node = undefined
            return true
        }
    }
    
    let c = word[index]
    let child = node.children[c.charCodeAt() - 'a'.charCodeAt()]
    let signal = false
    if(node.val === "root"){
        erase(child, word, index+1)
    }else if(index < word.length -1){
        signal = erase(child, word, index+1)
    }else if(index === word.length -1){
        signal = true
    }
    
    if(signal && !child.terminates){
        node.children[c.charCodeAt() - 'a'.charCodeAt()] = undefined
    }else if(signal && child.terminates){
        child.count = child.count - 1
        if(!child.count) child.terminates = false
        signal = false
    }
    return signal
}

Trie.prototype.erase = function(word) {
    erase(this.root, word, 0)
};
```

### SearchWordSimilarTo

```
function search(root, word, index){
    let curr = root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(c!=='.'){
            if(curr.children[c.charCodeAt() - 'a'.charCodeAt()] === undefined){
                return null
            }
            curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
        }else{
            
        }
    }
}

WordDictionary.prototype.search = function(word) {
    return search(this.root, word, 0)
};
```