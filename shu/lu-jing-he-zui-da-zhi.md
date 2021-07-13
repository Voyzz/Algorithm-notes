# 【路径和】最大值

[二叉树中的最大路径和](https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/)

给定一个非空二叉树，返回其最大路径和。 本题中，路径被定义为一条从树中任意节点出发，达到任意节点的序列。该路径至少包含一个节点，且不一定经过根节点。

```javascript
var maxPathSum = function(root) {
    let max = -Infinity;
    function dfs(root){
        if(!root) return 0;
        let l = Math.max(dfs(root.left),0);
        let r = Math.max(dfs(root.right),0);
        max = Math.max(max,l + r + root.val);
        return Math.max(l,r)+root.val;
    }
    dfs(root);
    return max;
};
```

