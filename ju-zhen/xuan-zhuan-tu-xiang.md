# 旋转图像

[旋转图像](https://leetcode-cn.com/problems/rotate-image/)

给定一个 n × n 的二维矩阵表示一个图像。 将图像顺时针旋转 90 度

```javascript
var rotate = function(matrix) {
    if(!matrix.length) return [];
    let left = 0,right = matrix.length-1;
    while(right-left > 0){
        [matrix[left],matrix[right]] = [matrix[right],matrix[left]];
        left++;
        right--;
    }
    for(let i = 0;i < matrix.length;i++){
        for(let j = i+1;j < matrix[i].length;j++){
            [matrix[i][j],matrix[j][i]] = [matrix[j][i],matrix[i][j]];
        }
    }
    return matrix;
};
```

