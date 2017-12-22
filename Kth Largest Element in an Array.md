# Kth Largest Element in an Array
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
For example,
Given [3,2,1,5,6,4] and k = 2, return 5.

#### Note: 
You may assume k is always valid, 1 ≤ k ≤ array's length.

#### Credits:
Special thanks to @mithmatt for adding this problem and creating all test cases.

```apple js
function findKthLargest(nums, k) {
    let nNums = nums.sort(function (a, b) {
        return a - b;
    });
    let inx = nNums.length - k;
    let num = nNums.slice(inx, inx + 1)[0];
    return num
}
```