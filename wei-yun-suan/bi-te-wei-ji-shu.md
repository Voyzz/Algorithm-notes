# 比特位计数

[比特位计数](https://leetcode-cn.com/problems/counting-bits/)

给定一个非负整数 num。对于 0 ≤ i ≤ num 范围中的每个数字 i ，计算其二进制数中的 1 的数目并将它们作为数组返回



1. 奇数1的个数等于前一个偶数＋1
2. 偶数1的个数等于当前偶数 &gt;&gt; 1 的值

```javascript
var countBits = function(num) {
    let res = [0];
    for(let i = 1;i <= num;i++){
        if(i & 1){
            res[i] = res[i-1] + 1;
        }else{
            res[i] = res[i >> 1];
        }
    }
    return res;
};
```

