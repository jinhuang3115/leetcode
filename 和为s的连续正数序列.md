~~~~//输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。 
//
// 序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。 
//
// 
//
// 示例 1： 
//
// 输入：target = 9
//输出：[[2,3,4],[4,5]]
// 
//
// 示例 2： 
//
// 输入：target = 15
//输出：[[1,2,3,4,5],[4,5,6],[7,8]]
// 
//
// 
//
// 限制： 
//
// 
// 1 <= target <= 10^5 
// 
//


//leetcode submit region begin(Prohibit modification and deletion)
/**
 * @param {number} target
 * @return {number[][]}
 */
var findContinuousSequence = function(target) {
    const mid = target % 2 ? Math.floor(target / 2) + 1 : target / 2;
    let res = [];
    let arr = [];
    let sum = 0;
    for (let i = 1; i <= mid; i++){
        arr.push(i);
        sum += i;
        while(sum > target){
            sum -= arr[0];
            arr.shift();
        }
        if (sum === target && arr.length > 1){
            res.push([...arr]);
        }
    }
    return res;
};
//leetcode submit region end(Prohibit modification and deletion)
