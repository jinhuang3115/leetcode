# Power of Four
Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

判断一个数是否是4个次方
1. 先判断是否是2的次方 num & (num - 1) 如果是0，就是2的次方
2. 再判断是否是4的次方 (num - 1) % 3  4的次方可以整除3

````
var num = 64;
function isPowerOfFour(num){
    return (num > 0 && !(num & (num - 1)) && !((num - 1) % 3));
}

isPowerOfFour(num);
````