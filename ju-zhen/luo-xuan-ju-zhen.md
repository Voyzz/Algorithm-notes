# 螺旋矩阵

[螺旋矩阵 II](https://leetcode-cn.com/problems/spiral-matrix-ii/)

给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵

```javascript
var generateMatrix = function(n) {
    let rows = n-1,cols = n-1,col = 0,row = 0,iter = 1,x_dire = 1,y_dire = 1,cur_dire = 1,res = [];
    for(let i = 0;i < n;i++) res.push([]);
    while(iter <= n ** 2) {
        if (cur_dire === 1 && res[row][col] === undefined) {
            res[row][col] = iter;
            iter++;
            if (x_dire === 1) {
                if (col < cols) {
                    col++;
                } else {
                    cur_dire = -1;
                    x_dire = -x_dire;
                    if (y_dire === 1) row++;
                    else row--;
                }
            } else {
                if (col > 0) {
                    col--;
                } else {
                    cur_dire = -1;
                    x_dire = -x_dire;
                    if (y_dire === 1) row++;
                    else row--;
                }
            }
        }else if (cur_dire === 1 && res[row][col]) {
            if (y_dire === 1) row++;
            else row--;
            x_dire = -x_dire;
            cur_dire = -1;
            if (x_dire === 1) col++;
            else col--;
        }else if (cur_dire === -1 && res[row][col] === undefined) {
            res[row][col] = iter;
            iter++;
            if (y_dire === 1) {
                if (row < rows) {
                    row++;
                } else {
                    cur_dire = 1;
                    y_dire = -y_dire;
                    if (x_dire === 1) col++;
                    else col--;
                }
            } else {
                if (row >= 0) {
                    row--;
                } else {
                    cur_dire = 1;
                    y_dire = -y_dire;
                    if (x_dire === 1) col++;
                    else col--;
                }
            }
        } else if(cur_dire === -1 && res[row][col]) {
            if (x_dire === 1) col++;
            else col--;
            y_dire = -y_dire;
            cur_dire = 1;
            if (y_dire === 1) row++;
            else row--;
        }
    }
    return res;
};
```

