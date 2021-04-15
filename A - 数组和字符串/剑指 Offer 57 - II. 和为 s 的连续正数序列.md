# 剑指 Offer 57 - II. 和为 s 的连续正数序列
## 题目
```

输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

 

示例 1：

输入：target = 9
输出：[[2,3,4],[4,5]]
示例 2：

输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
 

限制：

1 <= target <= 10^5
```

## 题解
### 滑动窗口
```
/**
 * @param {number} target
 * @return {number[][]}
 */
var findContinuousSequence = function(target) {
    if(target == 1) return [[1]];

    let _left = 1,
        _right = 2,
        res = [];
    
    // 等差数列和大于目标值则缩小窗口（左侧+1）
    // 小于则扩大窗口（右侧+1）
    while(_right < target){
        const sum = (_left+_right)*(_right-_left+1)/2;
        if(sum == target){
            const item = []
            for(let i=_left;i<_right+1;i++){
                item.push(i)
            };
            res.push(item);
            _left++;
        }else if(sum < target){
            _right++
        }else{
            _left++
        }
    }

    return res;
};
```