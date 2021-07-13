# 【路径和】为某一值的集合

[二叉树中和为某一值的路径](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

输入一棵二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径。

```javascript
// 路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。(注意: 在返回值的list中，数组长度大的数组靠前)
//1. dfs + 回溯
//2. 深度搜索路径，将路径中的每个节点值相加，路径存入缓存，直到遍历到最深处
//3. 比较当前值是否为目标值，如果是将缓存的路径加入结果数组，如果不是则回退到上一个节点

function dfs(root,expectNumber,cur,path,result) {
    cur += root.val;
    path.push(root);
    if(cur === expectNumber && root.left === null && root.right === null){
        result.push(path.slice(0));
    }
    root.left && dfs(root.left,expectNumber,cur,path,result);
    root.right && dfs(root.right,expectNumber,cur,path,result);
    //重要
    path.pop();
}
function FindPath(root, expectNumber)
{
    let result = [],path = [],cur = 0;
    if(!root) return result;
    dfs(root,expectNumber,cur,path,result);
    return result;
}
```

