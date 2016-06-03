# leetcode
leetcode解题

For example,

Given s = "the sky is blue",

return "blue is sky the".

给一个输入的字符串，单词反向排序输出

``` 
var reverseWords = function(str) {
    var arr = str.trim().split(" ");
    var narr = [];
    for (var i = arr.length; i--;){
        if (arr[i]){
          narr.push(arr[i]);
        }
    }
     return narr.join(" ");
};
```
