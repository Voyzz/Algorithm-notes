# 无重叠区间

## LeetCode 435. 无重叠区间

### 题目

```text
给定一个区间的集合，找到需要移除区间的最小数量，使剩余区间互不重叠。

注意:

可以认为区间的终点总是大于它的起点。
区间 [1,2] 和 [2,3] 的边界相互“接触”，但没有相互重叠。
示例 1:

输入: [ [1,2], [2,3], [3,4], [1,3] ]

输出: 1

解释: 移除 [1,3] 后，剩下的区间没有重叠。
示例 2:

输入: [ [1,2], [1,2], [1,2] ]

输出: 2

解释: 你需要移除两个 [1,2] 来使剩下的区间没有重叠。
示例 3:

输入: [ [1,2], [2,3] ]

输出: 0

解释: 你不需要移除任何区间，因为它们已经是无重叠的了。
```

### 题解

* 算出这些区间中最多有几个互不相交的区间
* 从区间集合 intvs 中选择一个区间 x，这个 x 是在当前所有区间中结束最早的（end 最小）。
* 把所有与 x 区间相交的区间从区间集合 intvs 中删除。
* 重复步骤 1 和 2，直到 intvs 为空为止。之前选出的那些 x 就是最大不相交子集

#### 递归

```javascript
var eraseOverlapIntervals = function(intervals) {
    if(intervals.length<2) return 0;

    intervals.sort((a,b)=>a[1]-b[1])

    let count = 1,
        _end = intervals[0][1];

    for(const inter of intervals){
        const _start = inter[0];
        if(_start >= _end){
            _end = inter[1];
            count++
        }
    }

    return intervals.length - count

};
```

