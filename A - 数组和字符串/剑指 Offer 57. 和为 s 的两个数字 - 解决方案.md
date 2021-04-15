# 剑指 Offer 57. 和为 s 的两个数字 - 解决方案

## 题目
```
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

 

示例 1：

输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
示例 2：

输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
```

## 题解
### 双指针
```
function twoSum(nums: number[], target: number): number[] {
    let _left:number = 0,
        _right:number = nums.length-1;
    
    // 左边数字和右边数字相加 
    // 和小于目标则左指针+1
    // 和大于目标则右指针-1
    while(_left <= _right){
        const sum:number = nums[_left]+nums[_right];
        if(sum<target) _left++;
        else if(sum>target) _right--;
        else return [nums[_left],nums[_right]];
    }
};
```