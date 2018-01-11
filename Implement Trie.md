# Implement Trie 字典树

Implement a trie with insert, search, and startsWith methods.

Note:

You may assume that all inputs are consist of lowercase letters a-z.

```apple js
/**
 * Initialize your data structure here.
 */
function TrieNode(){
    return {
        next: {},
        isWord: false
    }
}
var Trie = function() {
    this.root = new TrieNode();
};

/**
 * Inserts a word into the trie. 
 * @param {string} word
 * @return {void}
 */
Trie.prototype.insert = function(word) {
    let root = this.root;
    let w = "";
      for(let i = 0, len = word.length; i < len; i++){
        w = word[i];
        if(!(w in root.next)){
            root.next[w] = new TrieNode();
        }
        root = root.next[w];
    }
    root.isWord = true;
};

/**
 * Returns if the word is in the trie. 
 * @param {string} word
 * @return {boolean}
 */
Trie.prototype.search = function(word) {
    let root = this.root;
    let w = "";
    for(let i = 0, len = word.length; i < len; i++){
        w = word[i];
        if(!(w in root.next)){
            return false;
        }
        root = root.next[w];
    }
    return root.isWord;
};

/**
 * Returns if there is any word in the trie that starts with the given prefix. 
 * @param {string} prefix
 * @return {boolean}
 */
Trie.prototype.startsWith = function(prefix) {
    let root = this.root;
    let w = "";
     for(let i = 0, len = prefix.length; i < len; i++){
        w = prefix[i];
        if(!(w in root.next)){
            return false;
        }
        root = root.next[w];
    }
    return true;
};

/** 
 * Your Trie object will be instantiated and called as such:
 * var obj = Object.create(Trie).createNew()
 * obj.insert(word)
 * var param_2 = obj.search(word)
 * var param_3 = obj.startsWith(prefix)
 */
```