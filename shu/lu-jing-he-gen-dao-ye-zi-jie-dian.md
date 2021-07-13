# 【路径和】根到叶子节点

给定一个二叉树，它的每个结点都存放一个 0-9 的数字，每条从根到叶子节点的路径都代表一个数字。 例如，从根到叶子节点路径 1-&gt;2-&gt;3 代表数字 123。 计算从根到叶子节点生成的所有数字之和。 说明: 叶子节点是指没有子节点的节点。

```javascript
// 简单的dfs
var sumNumbers = function(root) {
  let res = 0;
  function dfs(root,temp) {
      if(!root) return;
      temp += root.val;
      if((!root.left) && (!root.right)) res += Number(temp);
      dfs(root.left,temp);
      dfs(root.right,temp);
  }
  dfs(root,'');
  return res;
};
```

