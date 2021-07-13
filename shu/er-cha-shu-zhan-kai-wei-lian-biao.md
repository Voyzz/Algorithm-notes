# 【二叉树】展开为链表

## LeetCode 114. 二叉树展开为链表

### 题目

```text
给你二叉树的根结点 root ，请你将它展开为一个单链表：

展开后的单链表应该同样使用 TreeNode ，其中 right 子指针指向链表中下一个结点，而左子指针始终为 null 。
展开后的单链表应该与二叉树 先序遍历 顺序相同。


示例 1：


输入：root = [1,2,5,3,4,null,6]
输出：[1,null,2,null,3,null,4,null,5,null,6]
示例 2：

输入：root = []
输出：[]
示例 3：

输入：root = [0]
输出：[0]
```

### 题解

#### 递归

```javascript
var flatten = function(root) {
    // 函数意义：展开以root为结点的二叉树
    // root结点要做什么：
    // [后序遍历]
    // 1.左子树展开，右子树展开
    // 2.把展开的左子树挂在root右子树，展开的右子树挂在其右子树

    // [base case] 结点为空，停止操作
    if(root == null) return null;

    // [后序遍历] 展开左右子树
    flatten(root.left);
    flatten(root.right);

    // [根节点操作]
    const _right = root.right;
    root.right = root.left;
    root.left = null;

    let p = root;
    while(p.right != null){
        p = p.right;
    }
    p.right = _right;

    // 返回根节点
    return root;
};
```

