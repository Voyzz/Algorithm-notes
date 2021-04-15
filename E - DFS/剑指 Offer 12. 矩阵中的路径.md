# 剑指 Offer 12. 矩阵中的路径
## 题目
```
请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中的任意一格开始，每一步可以在矩阵中向左、右、上、下移动一格。如果一条路径经过了矩阵的某一格，那么该路径不能再次进入该格子。例如，在下面的3×4的矩阵中包含一条字符串“bfce”的路径（路径中的字母用加粗标出）。

[["a","b","c","e"],
["s","f","c","s"],
["a","d","e","e"]]

但矩阵中不包含字符串“abfb”的路径，因为字符串的第一个字符b占据了矩阵中的第一行第二个格子之后，路径不能再次进入这个格子。

 

示例 1：

输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
示例 2：

输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
 

提示：

1 <= board.length <= 200
1 <= board[i].length <= 200
注意：本题与主站 79 题相同：https://leetcode-cn.com/problems/word-search/

相关标签
深度优先搜索
```

## 题解
### DFS 递归
```
/**
 * @param {character[][]} board
 * @param {string} word
 * @return {boolean}
 */
var exist = function(board, word) {
    // 遍历以每一个元素为起始进行dfs
    for(let i=0;i<board.length;i++){
        for(let j=0;j<board[0].length;j++){
            if(dfs(board,word,i,j,0)) return true;
        }
    }
    return false;
};

const dfs = function(board,word,i,j,level){
    // 截止条件：越界 或当前level字母不等于该字母
    if(i>board.length-1 || i<0 || j>board[0].length-1 || j<0 || word[level] != board[i][j]) return false;
    // dfs至最底层仍不截止则返回true
    if(level == word.length-1) return true;
    
    // 暂存当前字母
    const tmp = board[i][j];
    // 标记已使用过的字母
    board[i][j] = "/";
    // 上右下左递归
    const res = dfs(board,word,i-1,j,level+1) || dfs(board,word,i,j+1,level+1) || dfs(board,word,i+1,j,level+1) || dfs(board,word,i,j-1,level+1);
    // 回溯：将当前位置的标记还原
    board[i][j] = tmp;
    return res;
}
```