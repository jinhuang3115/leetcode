# leetcode 解题
### 1. Reverse Words in a String
#### 难度：中等
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
### 2. Range Sum Query - Immutable
#### 难度：简单
Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.<br>

Example:
```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```

##### Note:
1. You may assume that the array does not change.
2. There are many calls to sumRange function.
 
数组求和，已知数组不会改变，sumRange会被调用很多次

```
var NumArray = function(nums) {
    var rangeSum;
    
        rangeSum = [0];
        var sum = 0;
        for (var g = 0, len = nums.length; g < len; g++){
            sum += nums[g];
            rangeSum.push(sum);
        }
    
    this.rangeSum = rangeSum;
};

/**
 * @param {number} i
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
    return this.rangeSum[j + 1] - this.rangeSum[i];
};
```

### 3. Word Pattern
#### 难度：简单
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
