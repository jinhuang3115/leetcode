# Word Pattern
Given a `pattern` and a string `str`, find if `str` follows the same `pattern`.<br>
Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.<br>

#####Examples:
```
pattern = "abba", str = "dog cat cat dog" should return true.
pattern = "abba", str = "dog cat cat fish" should return false.
pattern = "aaaa", str = "dog cat cat dog" should return false.
pattern = "abba", str = "dog dog dog dog" should return false.
```
#####Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

```
var wordPattern = function(pattern, str) {
    var arr = str.split(" ");
    var patternArr = pattern.split('');
    var parObj = {};
    var arrObj = {};
    var parrArr = [];
    var arrArr = [];
    for (var i = 0, len = patternArr.length; i < len; i++) {
        if (!parObj[patternArr[i]]) {
            parObj[patternArr[i]] = [];
            parrArr.push(i);
        }
    }
    for (var j = 0, jlen = arr.length; j < jlen; j++) {
        if (!arrObj[arr[j]]) {
            arrObj[arr[j]] = [];
            arrArr.push(j);
        }
    }
   return (parrArr.length === arrArr.length && arr.length === patternArr.length);
};
```