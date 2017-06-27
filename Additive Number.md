# Additive Number
Additive number is a string whose digits can form additive sequence.

A valid additive sequence should contain at least three numbers. Except for the first two numbers, each subsequent number in the sequence must be the sum of the preceding two.

For example:
"112358" is an additive number because the digits can form an additive sequence: 1, 1, 2, 3, 5, 8.

1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, 3 + 5 = 8
"199100199" is also an additive number, the additive sequence is: 1, 99, 100, 199.
1 + 99 = 100, 99 + 100 = 199
Note: Numbers in the additive sequence cannot have leading zeros, so sequence 1, 2, 03 or 1, 02, 3 is invalid.

Given a string containing only digits '0'-'9', write a function to determine if it's an additive number.

````
var num = "112358";
var num1 = "199100199";
var num2 = "101";

var isAdditiveNumber = function (num) {
    var n = num.length;
    for (var i = 1; i <= n / 2; i++) {
        for (var j = 1; Math.max(j, i) <= n - i - j; j++) {
            if (isValid(i, j, num)) {
                return true;
            }
        }
    }
    return false;

    function isValid(i, j, num) {
        if (num.charAt(0) == '0' && i > 1) {
            return false;
        }
        if (num.charAt(i) == '0' && j > 1) {
            return false;
        }
        var sum;
        var n1 = parseInt(num.substring(0, i), 10);
        var n2 = parseInt(num.substring(i, i + j), 10);
        for(var h = i + j; h != num.length; h += sum.length){
            n2 = n2 + n1;
            n1 = n2 - n1;
            sum = n2.toString();
            if(!(num.substring(h,h + sum.length) === sum)){
                return false;
            }
        }
        return true;
    }
};

console.log(isAdditiveNumber(num1));
````