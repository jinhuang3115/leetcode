# Custom Sort String

S and T are strings composed of lowercase letters. In S, no letter occurs more than once.

S was sorted in some custom order previously. We want to permute the characters of T so that they match the order that S was sorted. More specifically, if x occurs before y in S, then x should occur before y in the returned string.

Return any permutation of T (as a string) that satisfies this property.
```apple js
Example :
Input: 
S = "cba"
T = "abcd"
Output: "cbad"
Explanation: 
"a", "b", "c" appear in S, so the order of "a", "b", "c" should be "c", "b", and "a". 
Since "d" does not appear in S, it can be at any position in T. "dcba", "cdba", "cbda" are also valid outputs.
```

Note:

1. S has length at most 26, and no character is repeated in S.
2. T has length at most 200.
3. S and T consist of lowercase letters only.

```apple js
function customSortString(S, T) {
    let tempArr = [];
    let temMap = {};
    T = T.split("");
    S = S.split("");
    for(let i = 0, len = T.length; i < len; i++){
        let li = T[i];
        let inx = S.indexOf(li);
        if (inx > -1){
            if (typeof temMap[li] !== 'undefined'){
                let nInx = inx + 1;
                temMap[li] = nInx;
                tempArr.splice(nInx, 0, li);
                S.splice(nInx, 0, li);
            }else{
                temMap[li] = inx;
                tempArr[inx] = li;
            }
            T.splice(i, 1);
            i--;
            len--;
        }
    }
    return tempArr.concat(T).join("");
}
```


