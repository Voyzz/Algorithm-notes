# 长度最小的连续子数组

给定一个含有 n 个正整数的数组和一个正整数 s ，找出该数组中满足其和 ≥ s 的长度最小的连续子数组，并返回其长度。如果不存在符合条件的连续子数组，返回 0。

```javascript
// 滑动窗口的解法
// 每次将右指针对应的数添加到临时num中
// 查看是否满足题意，满足则作为一个可行解与len作比较，同时移动左指针
// 移动右指针到下一个位置


var minSubArrayLen = function(s, nums) {
    let left = 0, right = 0, len = Infinity, num = 0;
    while(right < nums.length) {
        num += nums[right];
        while(num >= s) {
            len = Math.min(len, right - left + 1);
            num -= nums[left];
            left++;
        }
        right++;
    }
    return len === Infinity ? 0 : len;
};
```

