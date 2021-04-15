# 剑指 Offer 29. 顺时针打印矩阵
## 题目
```
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

 

示例 1：

输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
示例 2：

输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
 

限制：

0 <= matrix.length <= 100
0 <= matrix[i].length <= 100
```

## 题解
```
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
    if(matrix.length == 0) return [];

    let _top = 0,
        _right = matrix[0].length-1,
        _bottom = matrix.length-1,
        _left = 0,
        res = [];

    // 动态更新边界值 直至越界
    while(true){
        for(let i=_left;i<=_right;i++) res.push(matrix[_top][i])
        if(++_top > _bottom) break;
        for(let i=_top;i<=_bottom;i++) res.push(matrix[i][_right])
        if(--_right < _left) break;
        for(let i=_right;i>=_left;i--) res.push(matrix[_bottom][i])
        if(--_bottom < _top) break;
        for(let i=_bottom;i>=_top;i--) res.push(matrix[i][_left])
        if(++_left > _right) break;       
    }

    return res;
};
```