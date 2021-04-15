# 剑指 Offer 21. 调整数组顺序使奇数位于偶数前面

## 题目
```
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。

 

示例：

输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
 

提示：

1 <= nums.length <= 50000
1 <= nums[i] <= 10000
```

## 题解
### 双指针 位置交换
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var exchange = function(nums) {
    // 双指针指向头和尾
    let _left = 0,_right = nums.length - 1;

    while(_left<_right){
        // 找到最前面的偶数
        while(nums[_left]%2 == 1 && _left<_right){
            _left++
        }
        // 找到最后面的奇数
        while(nums[_right]%2 == 0 && _left<_right){
            _right--
        }
        /* 
        交换 【最前面的偶数】 和 【最后面的奇数】
        直至左右指针相遇即为遍历完
        */
        [nums[_left],nums[_right]] = [nums[_right],nums[_left]]
    }

    return nums
};
```