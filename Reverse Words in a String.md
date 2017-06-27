# Reverse Words in a String
Given an input string, reverse the string word by word.<br>
For example,<br>
Given s = "the sky is blue",<br>
return "blue is sky the".<br>
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

