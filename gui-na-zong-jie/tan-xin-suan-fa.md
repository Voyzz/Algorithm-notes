# 贪心算法

## 思想

* 贪心算法可以认为是动态规划算法的一个特例
* 每一步都做出一个**局部最优**的选择，最终的结果就是**全局最优**

## 框架

* 贪心算法没有固定解法套路
* 以【最多有多少无重叠区间】为例
  * 1. 从区间集合 intvs 中选择一个区间 x，这个 x 是在当前所有区间中结束最早的（end 最小）。
  * 2. 把所有与 x 区间相交的区间从区间集合 intvs 中删除。
  * 3. 重复步骤 1 和 2，直到 intvs 为空为止。之前选出的那些 x 就是最大不相交子集

```javascript
var eraseOverlapIntervals = function(intervals) {
    if(intervals.length<2) return intervals.length;

    // 递增排序
    intervals.sort((a,b)=>a[1]-b[1])

    let count = 1,
        _end = intervals[0][1];

    for(const inter of intervals){
        const _start = inter[0];
        // 无重合则count+1 重置右边界
        if(_start >= _end){
            _end = inter[1];
            count++
        }
    }
    return count
};
```



