# Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

一个数字数组，这个数组中的2个值相加的和等于一个指定的目标数字。

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
   var map = {};
       for (var i = 0, len = nums.length; i < len; i++) {
           var num = target - nums[i];
           if (map[num]) {
              return[nums[i], num];
           }
           map[nums[i]] = i;
       }
};

```
创建一个map对象，每次在循环中以数组当前值为键存入map对象中。
在循环中，判断目标数字target减去当前循环的值nums[i]是否存在于map对象中，
如果存在，就说明当前循环的值与存在于map中的值相加等于目标值target，就return出去.

