# 矩阵查找

## 剑指 Offer 04. 二维数组中的查找

### 题目

```javascript
在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。



示例:

现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。



限制：

0 <= n <= 1000

0 <= m <= 1000
```

### 解答

```javascript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var findNumberIn2DArray = function(matrix, target) {
    if(matrix.length == 0) return false;

    // 从数组的左下角开始
    let x = 0,y = matrix.length - 1;

    // 越界则说明无此数
    while(x<matrix[0].length && y>=0){
        if(target == matrix[y][x]){
            return true;
        }
        // 比目标数大则向上
        else if(target > matrix[y][x]){
            x++;
        }
        // 比目标数小则像右
        else if(target < matrix[y][x]){
            y--
        }
    }

    return false
};
```

