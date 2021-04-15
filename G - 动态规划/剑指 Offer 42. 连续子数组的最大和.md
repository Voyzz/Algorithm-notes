# 剑指 Offer 42. 连续子数组的最大和
## 题目
```
输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

 

示例1:

输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
 

提示：

1 <= arr.length <= 10^5
-100 <= arr[i] <= 100
注意：本题与主站 53 题相同：https://leetcode-cn.com/problems/maximum-subarray/

 

相关标签
分治算法
动态规划
```

## 题解
### DP
```
// 状态转移方程 :dp[i]表示以下标i为结尾的子数组的最大和
// dp[i-1]为正: dp[i] = dp[i-1] + nums[i];
// dp[i-1]为负: dp[i] = nums[i];
function maxSubArray(nums: number[]): number {
    let res:number = nums[0];

    for(let i:number=1;i<nums.length;i++){
        if(nums[i-1] > 0){
            nums[i] += nums[i-1];
        }
        res = Math.max(nums[i],res);
    }

    return res;
};
```