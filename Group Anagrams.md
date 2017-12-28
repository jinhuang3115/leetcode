#Group Anagrams
Given an array of strings, group anagrams together.

For example, given: ["eat", "tea", "tan", "ate", "nat", "bat"], 
Return:
```apple js
[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

### Note: 
All inputs will be in lower-case.

```apple js
var groupAnagrams = function(strs) {
    let result = [];
    let argkey = {};
    let count = 0;
    for(let i = 0, len = strs.length; i < len; i++){
           let str = strs[i];
        let nstr = str.split("").sort().join("");
        let val = argkey[nstr];
        if (typeof val === 'undefined'){
            result.push([str]);
            argkey[nstr] = count++;
        }else{
            result[val].push(str)
        }
    }
    return result;
};
```
