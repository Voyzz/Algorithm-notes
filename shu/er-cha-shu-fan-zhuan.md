# 【二叉树】翻转

## LeetCode 226. 翻转二叉树

### 题目

```text
翻转一棵二叉树。

示例：

输入：

     4
   /   \
  2     7
 / \   / \
1   3 6   9
输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

### 题解

#### 递归

```javascript
var invertTree = function(root) {
    // 函数意义：翻转以root为结点的二叉树
    // root结点要做什么：调换左右节点

    // [base case] 结点为空，停止操作
    if(root == null) return root;

    // [前序遍历][根节点操作] 调换左右节点
    [root.left,root.right] = [root.right,root.left];

    // 遍历子节点
    invertTree(root.left);
    invertTree(root.right);

    // 返回根节点
    return root;
};
```

