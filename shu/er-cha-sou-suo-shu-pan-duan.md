# 【二叉搜索树】判断

[验证二叉搜索树](https://leetcode-cn.com/problems/validate-binary-search-tree/)

给定一个二叉树，判断其是否是一个有效的二叉搜索树。

```javascript
let pre = -Infinity;
var isValidBST = function(root) {
    if(!root) return true;
    let left = isValidBST(root.left);
    if(root.val <= pre || !left) return false;
    pre = root.val;
    return isValidBST(root.right);
};
```

