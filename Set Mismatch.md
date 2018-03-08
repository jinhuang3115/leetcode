# Set Mismatch
The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.

##### Example 1:
````
Input: nums = [1,2,2,4]
Output: [2,3]
````
##### Note:
1. The given array size will in the range [2, 10000].
2. The given array's numbers won't have any order.

```apple js
function findErrorNums(nums) {
    let nNums = nums.sort();
    let reNumsMap = {};
    let errorNums = [];
    let sum1 = 0;
    for(let i = 0, len = nNums.length; i < len; i++){
        let num = nNums[i];
        if (!reNumsMap[num]){
            reNumsMap[num] = num;
            sum1 += num;
        }else{
            errorNums.push(num);
        }
    }
    let keys = Object.keys(reNumsMap);
    let min = parseInt(keys[0], 10);
    let max = parseInt(keys[keys.length - 1], 10);
    let sum = (min + max)*(max - min + 1) / 2;
    let misNum = sum - sum1;
    if (!misNum){
        if (min > 1){
            errorNums.push(1);
        }else{
            errorNums.push(max + 1);
        }
    }else{
        errorNums.push(misNum);
    }
    return errorNums;
}
```