# 剑指 Offer 39. 数组中出现次数超过一半的数字

## 题目

```JavaScript
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

 

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

 

示例 1:

输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
 

限制：

1 <= 数组长度 <= 50000
```

## 题解

### 摩尔投票

```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    let count = 0,curr = 0;

    // 用不同的数字去抵消当前数字 留下的就是超半数的数字
    for(const num of nums){
        if(count == 0){
            curr = num
        }
        if(curr == num){
            count++
        }else{
            count--
        }
    }

    return curr
};
```

### 哈希

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    let n = nums.length,
        hashMap = new Map();

    for(let i=0;i<n;i++){
        let count;
        if(hashMap.has(nums[i])){
            count = hashMap.get(nums[i]);
        }else{
            count = 0
        }
        if(count+1 > (n/2)) return nums[i];
        hashMap.set(nums[i],count+1)
    }
};
```

## 排序

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    return nums.sort()[nums.length>>1]
};
```
