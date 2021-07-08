# 岛屿数量

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
    // 边界处理
    if(grid.length == 0) return 0;


    let row = grid.length,
        column  = grid[0].length,
        len = grid.length,
        res = 0;
    
    const DFS = (grid,i,j) => {
        // base case (递归终止条件)
        if(i<0 || j< 0 || i>row-1 || j>column-1 || grid[i][j] == '0') return;


        // 将其变成水域
        grid[i][j] = '0';


        // 上下左右
        DFS(grid,i-1,j);
        DFS(grid,i,j+1);
        DFS(grid,i+1,j);
        DFS(grid,i,j-1);
    }


    // 遍历整个网格
    for(let r=0;r<row;r++){
        for(c=0;c<column;c++){
            if(grid[r][c] == '1'){
                res += 1;
                DFS(grid,r,c)
            }
        }
    }


    return res;
    
};
```

