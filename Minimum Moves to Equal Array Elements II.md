# Minimum Moves to Equal Array Elements II
给定一个非空数字数组，计算让数组中各个数值都相等的话，需要多少步，一次只能增加1或减小1。
数组最大为10000

```
var minMoves2 = function (nums) {
    nums.sort(function sortNumber(a, b) {
        return a - b
    });
    var count = 0;
    var medium = nums[Math.floor(nums.length / 2)];
    for (var i = 0, len = nums.length; i < len; i++){
        count += Math.abs(nums[i] - medium);
    }
    return count;
};
```

1. 现对数组排序
2. 计算出数组的中间值
3. 循环数组，中间值减去当前循环的值就是该值要操作的步数
4. 相加步数得出总步数


### 优化1
循环次数还可以减少
```
var minMoves2 = function (nums) {
    nums.sort(function sortNumber(a, b) {
        return a - b
    });
    var count = 0;
    var i = 0,
        j = nums.length - 1;
    while (i < j) {
        count += nums[j] - nums[i];
        i ++;
        j --;
    }
    return count;
};
```
数组中两端的数字变成中间值的步数等于尾端数字减去对应的首端数字。
