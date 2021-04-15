# 剑指 Offer 56 - I. 数组中数字出现的次数
## 题目
```
一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

 

示例 1：

输入：nums = [4,1,4,6]
输出：[1,6] 或 [6,1]
示例 2：

输入：nums = [1,2,10,4,1,4,3,3]
输出：[2,10] 或 [10,2]
 

限制：

2 <= nums.length <= 10000
```

## 题解
### 位运算
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var singleNumbers = function(nums) {
    // 得到这两个数的异或值
    let product = 0;
    for (const val of nums){
        product ^= val;
    }
    // _digit 为 0001 测试最后一位是否为1 直至测到最低的1位
    let _digit = 1;
    while((product & _digit) == 0){
        _digit <<= 1;
    }

    // 以最低位为1不同区分出两组数字，其中分别包含这两个数字
    let a = 0,b = 0;
    for (const val of nums){
        if(val & _digit) a ^= val;
        else b ^= val;
    }
    return [a,b]
    
};
```

### 数组
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var singleNumbers = function(nums) {
    const res = [];

    for (const val of nums){
        const i = res.indexOf(val)
        if(i == -1){
            res.push(val)
        }else{
            res.splice(i,1)
        }
    }

    return res;
    
};
```