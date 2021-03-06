# 剑指 Offer 53 - I. 在排序数组中查找数字 I

## 题目

```JavaScript
统计一个数字在排序数组中出现的次数。

 

示例 1:

输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
示例 2:

输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
 

限制：

0 <= 数组长度 <= 50000
```

## 题解

### 二分法

```JavaScript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    return getRightMargin(nums,target)-getRightMargin(nums,target-1)
};

// 二分法查找目标数的右边界 和 目标数-1的右边界
const getRightMargin = function(nums,target){
    let _left = 0,
        _right = nums.length-1;

    while(_left<=_right){
        const _mid = (_left+_right)>>1;
        if(target >= nums[_mid]){
            _left = _mid + 1;
        }else{
            _right = _mid - 1;
        }
    }

    return _left;
}
```
