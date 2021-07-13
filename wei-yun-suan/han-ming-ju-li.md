# 汉明距离

[汉明距离](https://leetcode-cn.com/problems/hamming-distance/)

两个整数之间的[汉明距离](https://baike.baidu.com/item/%E6%B1%89%E6%98%8E%E8%B7%9D%E7%A6%BB)指的是这两个数字对应二进制位不同的位置的数目。给出两个整数 x 和 y，计算它们之间的汉明距离

```javascript
var hammingDistance = function(x, y) {
    let ans = x ^ y,count = 0;
    while(ans){
        if(ans & 1) count++;
        ans = ans >> 1;
    }
    return count;
};
```

