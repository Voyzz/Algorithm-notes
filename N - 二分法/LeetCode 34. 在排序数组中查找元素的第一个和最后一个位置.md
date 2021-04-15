# LeetCode 34. 在排序数组中查找元素的第一个和最后一个位置
[34. 在排序数组中查找元素的第一个和最后一个位置](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
## 题目
```
给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值 target，返回 [-1, -1]。

进阶：

你可以设计并实现时间复杂度为 O(log n) 的算法解决此问题吗？
 

示例 1：

输入：nums = [5,7,7,8,8,10], target = 8
输出：[3,4]
示例 2：

输入：nums = [5,7,7,8,8,10], target = 6
输出：[-1,-1]
示例 3：

输入：nums = [], target = 0
输出：[-1,-1]
```

## 题解

### 二分法
```
function searchRange(nums: number[], target: number): number[] {
    return [findBound(nums,target,'left'),findBound(nums,target,'right')]
};

function findBound(nums: number[], target: number,dir:string):number{
    let _left:number = 0,
        _right:number = nums.length-1;
    
    while(_left<=_right){
        const _mid = Math.floor(_left+(_right-_left)/2);
        if(target < nums[_mid]){
            _right = _mid-1
        }else if(target > nums[_mid]){
            _left = _mid+1
        }else{
            if(dir === 'left'){
                _right = _mid-1;
            }else{
                _left = _mid+1
            }
        }
    }

    if(dir === 'left'){
        if(_left<0 || nums[_left] != target) return -1;
        else return _left;
    }
    if(dir === 'right'){
        if(_right<0 || nums[_right] != target) return -1;
        else return _right;
    }
}
```