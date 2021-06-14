# [211. Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)

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



function searchHelper(node, word, index){
    if(index===word.length && node.terminates) return true
    else if(index===word.length && !node.terminates) return false
    let haschar = false
    let char = word[index]
    let children = node.children
    if(char === '.'){
        for(let i=0; i<children.length; i++){
            haschar = haschar || searchHelper(children[i], word, index+1)
        }
    }else{
        for(let i=0; i<children.length; i++){
            if(char===children[i].val){
                haschar = searchHelper(children[i], word, index+1)
            }
        }
    }
    
    return haschar
}

/**
 * Initialize your data structure here.
 */
var WordDictionary = function() {
    this.root = new TrieNode("root", [], false)
};

/** 
 * @param {string} word
 * @return {void}
 */
WordDictionary.prototype.addWord = function(word) {
    this.root = insertHelper(word, this.root, 0)
};

/** 
 * @param {string} word
 * @return {boolean}
 */
WordDictionary.prototype.search = function(word) {
    return searchHelper(this.root, word, 0)
};

/** 
 * Your WordDictionary object will be instantiated and called as such:
 * var obj = new WordDictionary()
 * obj.addWord(word)
 * var param_2 = obj.search(word)
 */
```