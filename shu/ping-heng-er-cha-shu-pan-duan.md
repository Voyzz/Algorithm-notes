# 【平衡二叉树】判断



1. 比较两颗子树的高度，两边都取最大深度
2. 查看两颗子树高度差是否相差为1
3. 如果大于1，那么将其标记为-1（表示不是AVL树），然后每次递归时先判断该节点的子树是否时AVL树

```javascript
function IsBalanced_Solution(pRoot)
{
    return orderTree(pRoot) !== -1;
}
function orderTree(root) {
    if(!root) return 0;
    let left = orderTree(root.left);
    let right = orderTree(root.right);
    if(left === -1 || right === -1 || Math.abs(left-right) > 1) return -1;
    return Math.max(left,right)+1;
}
```

