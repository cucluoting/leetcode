# 208. Implement Trie (Prefix Tree)

Implement a trie with `insert`, `search`, and `startsWith` methods.

**Note:**  
You may assume that all inputs are consist of lowercase letters `a-z`.

```javascript
var TrieNode = function() {
  this.children = {}
  // 单词的结束标志
  this.isWord = false
};

/**
 * Initialize your data structure here.
 */
var Trie = function() {
  this.root = new TrieNode()
};

/**
 * Inserts a word into the trie. 
 * @param {string} word
 * @return {void}
 */
Trie.prototype.insert = function(word) {
  var node = this.root
  for (var i = 0, len = word.length; i < len; i++) {
    var char = word[i]
    // 如果还没有该字母则为该字母构造一个节点
    if (!node.children[char]) node.children[char] = new TrieNode()
    node = node.children[char]
  }
  node.isWord = true
};

/**
 * Returns if the word is in the trie. 
 * @param {string} word
 * @return {boolean}
 */
Trie.prototype.search = function(word) {
  var node = this.root
  for (var i = 0, len = word.length; i < len; i++) {
    var char = word[i]
    if (!node.children[char]) return false
    node = node.children[char]
  }
  return node.isWord
};

/**
 * Returns if there is any word in the trie that starts with the given prefix. 
 * @param {string} prefix
 * @return {boolean}
 */
Trie.prototype.startsWith = function(prefix) {
  var node = this.root
  for (var i = 0, len = prefix.length; i < len; i++) {
    var char = prefix[i]
    if (!node.children[char]) return false
    node = node.children[char]
  }
  return true
};

/** 
 * Your Trie object will be instantiated and called as such:
 * var obj = Object.create(Trie).createNew()
 * obj.insert(word)
 * var param_2 = obj.search(word)
 * var param_3 = obj.startsWith(prefix)
 */
```
