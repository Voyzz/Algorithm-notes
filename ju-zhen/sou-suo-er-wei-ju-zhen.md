# 搜索二维矩阵

[搜索二维矩阵 II](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/)

编写一个高效的算法来搜索 m x n 矩阵 matrix 中的一个目标值 target。该矩阵具有以下特性： 每行的元素从左到右升序排列。 每列的元素从上到下升序排列。

```javascript
输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
1. 选取左下角的值作为初始值key
2. 如果目标值大于key，因为是最左边的值（最小），所以col++
3. 如果目标值小于，那么更小的值只可能是上一行，所以row—

function Find(target,array){
    let rows = array.length;
    if(rows <= 0) return false;
    let cols = array[0].length;
    if(cols <= 0) return false;
    let row = rows - 1;
    let col = 0;
    while(row >= 0 && col < cols){
        if(array[row][col] > target){
            row--;
        }else if(array[row][col] < target){
            col++;
        }else{
            return true;
        }
    }
    return false;
}

```



