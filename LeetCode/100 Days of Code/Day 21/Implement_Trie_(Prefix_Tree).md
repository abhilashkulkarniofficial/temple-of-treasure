# [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)

## Solutions

### Solution 1

```
function TrieNode(val, children, terminates){
  this.val = val
  this.children = children
  this.terminates = terminates
}

function insertHelper(word, node, index){
  let children = node.children
  let i = 0
  let char = null
  let newNode = null

  while(char!==word[index] && i<children.length){
    newNode = children[i]
    char = newNode.val
    i++
  }

  if(char!==word[index]){
    if(index===word.length-1) newNode = new TrieNode(word[index], [], true)
    else newNode = new TrieNode(word[index], [], false)
    node.children.push(newNode)
  }else if(char===word[index] && index===word.length-1){
    newNode.terminates = true
  }

  if(index<word.length-1) insertHelper(word, newNode, index+1)
  return node

}

function searchHelper(root, word, startsWith){
  if(!root.children.length) return false
    let index = 0
    let haschar = true
    let node = root
    // console.log(node.val, node.terminates)
    while(index<word.length && haschar){
      let children = node.children
      haschar = false
      for(let i=0; i<children.length; i++){
          if(children[i].val===word[index]) {
              haschar = true
              node = children[i]
          }
      }
      // console.log(node.val, node.terminates)
      if(index===word.length-1 && !node.terminates && !startsWith) haschar = false
      index++
    }
    return haschar
}

var Trie = function(){
  this.root = new TrieNode("root",[],false)
}

Trie.prototype.insert = function(word){
  this.root = insertHelper(word, this.root, 0)
}

Trie.prototype.search = function(word) {
    return searchHelper(this.root, word, false)
    
};

Trie.prototype.startsWith = function(prefix) {
    return searchHelper(this.root, prefix, true)
};
```

### Solution 2

A much cleaner approach

```
function TrieNode(val, children, terminates){
    this.val = val
    this.children = children
    this.terminates = terminates
}

var Trie = function() {
    this.root = new TrieNode("root",new Array(26), false)
};

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
};

function getnode(word, root){
    let curr = root
    for(let i=0; i<word.length; i++){
        let c = word[i]
        if(!curr.children[c.charCodeAt() - 'a'.charCodeAt()]) return null
        curr = curr.children[c.charCodeAt() - 'a'.charCodeAt()]
    }
    return curr
}

Trie.prototype.search = function(word) {
    let node = getnode(word, this.root)
    return node !== null && node.terminates
};

Trie.prototype.startsWith = function(prefix) {
    return getnode(prefix, this.root) !== null
};
```