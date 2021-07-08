# 矩阵置零

[矩阵置零](https://leetcode-cn.com/problems/set-matrix-zeroes/)

给定一个 m x n 的矩阵，如果一个元素为 0，则将其所在行和列的所有元素都设为 0。请使用\*\*[原地](http://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)\*\*算法

```javascript
var setZeroes = function(matrix) {
    for(let i = 0;i < matrix.length;i++){
        for(let j = 0;j < matrix[i].length;j++){
            if(Object.is(matrix[i][j],0)){
                for(let k = 0;k < matrix.length;k++){
                    if(k !== i && Object.is(matrix[k][j],0)) continue;
                    else matrix[k][j] = -0
                }
                for(let k = 0;k < matrix[i].length;k++){
                    if(k !== j && Object.is(matrix[i][k],0)) continue;
                    else matrix[i][k] = -0
                }                
            }
        }
    }
    return matrix;
};
```

