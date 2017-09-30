
```
let arr = [2, 7, 6, 3, 8, 5];
function slove(arr) {
    let len = arr.length;
    let min = arr[0];
    let max = arr[len - 1];
    let sum = 0;
    for (let i = 1; i < len - 1; i++) {
        if (min < arr[i] && arr[i] < max) {
            sum += arr[i];
        }
    }
    sum = sum + min + max;
    /*let lowSum = (min * (min - 1)) / 2;
    let upSum = (max * (max + 1)) / 2;
    let sum1 = upSum - lowSum;*/
    let sum1 = (min + max)*(max - min + 1) / 2;
    return sum1 - sum;
}
slove(arr);
```
