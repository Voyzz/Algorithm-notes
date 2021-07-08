# 滑动窗口的最大值

## 剑指 Offer 59 - I. 滑动窗口的最大值

### 题目

```javascript
给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。

示例:

输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7


提示：

你可以假设 k 总是有效的，在输入数组不为空的情况下，1 ≤ k ≤ 输入数组的大小。

注意：本题与主站 239 题相同：https://leetcode-cn.com/problems/sliding-window-maximum/

相关标签
队列
Sliding Window
```

### 题解

#### 辅助队列

```javascript
function maxSlidingWindow(nums: number[], k: number): number[] {
    if(nums.length == 0 || k == 0) return [];

    const quene:number[] = [],res:number[] = [];

    for(let _left:number=1-k,_right:number=0;_right<nums.length;_left++,_right++){
        // 左侧丢掉的数字如果和队列头相等则丢弃
        if(_left > 0 && nums[_left-1] == quene[0]){
            quene.shift()
        }
        // 右侧数字进入队列，保持队列递减
        while(quene.length > 0 && quene[quene.length-1] < nums[_right]){
            quene.pop()
        }
        quene.push(nums[_right]);
        // 队列头为当前最大值
        if(_left >= 0) res.push(quene[0])
    }

    return res;
};
```

