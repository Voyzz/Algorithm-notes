# 缺失的数字

[0～n-1中缺失的数字](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字

```javascript
var missingNumber = function(nums) {
    let left = 0,
        right = nums.length - 1;
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        if (mid === nums[mid]) {
            left = mid + 1;
        } else if (mid < nums[mid]) {
            right = mid - 1;
        }
    }
    return left;
};
```

