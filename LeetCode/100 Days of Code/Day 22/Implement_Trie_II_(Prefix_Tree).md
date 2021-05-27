# [1804. Implement Trie II (Prefix Tree)](https://leetcode.com/problems/implement-trie-ii-prefix-tree/)

## Solutions

### Solution 1

```
function TrieNode(val, children, terminates){
    this.val = val
    this.children = children
    this.terminates = terminates
    this.count = 0
}


var Trie = function() {
    this.root = new TrieNode("root", new Array(26), false)
};

/** 
 * @param {string} word
 * @return {void}
 */
Trie.prototype.insert = function(word) {
    // console.log("insert: ",word)
    let curr = this.root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]){
            curr.children[c.charCodeAt() - 'a'.charCodeAt()] = new TrieNode(c, new Array(26), false)
        }
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    curr.terminates = true
    curr.count = curr.count+1
    // traverse(this.root, '')
};

/** 
 * @param {string} word
 * @return {number}
 */
function search(word, root){
    let curr = root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]) return null
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    return curr
}

Trie.prototype.countWordsEqualTo = function(word) {
    // console.log("countWordsEqualTo: ",word)
    let node = search(word, this.root)
    return node!==null?node.count:0
};

/** 
 * @param {string} prefix
 * @return {number}
 */

function countAllWords(node){
    if(!node.children.length) return node.count
    // console.log(node)
    let children = node.children
    let count = 0
    for(let i=0; i<children.length; i++){
        if(children[i]){
            count+=countAllWords(children[i])
        }
    }
    return count+node.count
}

Trie.prototype.countWordsStartingWith = function(prefix) {
    // console.log("countWordsStartingWith: ",prefix)
    let node = search(prefix, this.root)
    // let count = countAllWords(node)
    return node!==null?countAllWords(node):null
};

/** 
 * @param {string} word
 * @return {void}
 */
function lonely(node){
    for(let i=0; i<node.children.length; i++){
        if(node.children[i]) return false
    }
    return true
}

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

/** 
 * Your Trie object will be instantiated and called as such:
 * var obj = new Trie()
 * obj.insert(word)
 * var param_2 = obj.countWordsEqualTo(word)
 * var param_3 = obj.countWordsStartingWith(prefix)
 * obj.erase(word)
 */
```