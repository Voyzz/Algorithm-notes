---
description: 二分法框架
---

# 类型 - 二分法

## 例题

[704.二分查找（简单）](https://leetcode-cn.com/problems/binary-search)

[34.在排序数组中查找元素的第一个和最后一个位置（中等）](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

## 思路

1. 分析二分查找代码时，不要出现 else，全部展开成 else if 方便理解。
2. 注意「搜索区间」和 while 的终止条件，如果存在漏掉的元素，记得在最后检查。
3. 如需定义左闭右开的「搜索区间」搜索左右边界，只要在 nums\[mid\] == target 时做修改即可，搜索右侧时需要减一。
4. 如果将「搜索区间」全都统一成两端都闭，好记，只要稍改 nums\[mid\] == target 条件处的代码和返回的逻辑即可，推荐拿小本本记下，作为二分搜索模板。

## 模板

统一逻辑：左闭右闭区间

### 基本的二分查找

```go
int binary_search(int[] nums, int target) {
    int left = 0, right = nums.length - 1; 
    while(left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else if (nums[mid] > target) {
            right = mid - 1; 
        } else if(nums[mid] == target) {
            // 直接返回
            return mid;
        }
    }
    // 直接返回
    return -1;
}
```

### 寻找左边界

```go
int left_bound(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else if (nums[mid] > target) {
            right = mid - 1;
        } else if (nums[mid] == target) {
            // 别返回，锁定左侧边界
            right = mid - 1;
        }
    }
    // 最后要检查 left 越界的情况
    if (left >= nums.length || nums[left] != target)
        return -1;
    return left;
}
```

### 寻找右边界

```go
int right_bound(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else if (nums[mid] > target) {
            right = mid - 1;
        } else if (nums[mid] == target) {
            // 别返回，锁定右侧边界
            left = mid + 1;
        }
    }
    // 最后要检查 right 越界的情况
    if (right < 0 || nums[right] != target)
        return -1;
    return right;
}
```

