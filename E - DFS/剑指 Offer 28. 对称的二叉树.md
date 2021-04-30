# 剑指 Offer 28. 对称的二叉树

## 题目

```JavaScript
请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3

 

示例 1：

输入：root = [1,2,2,3,4,4,3]
输出：true
示例 2：

输入：root = [1,2,2,null,3,null,3]
输出：false
 

限制：

0 <= 节点个数 <= 1000

注意：本题与主站 101 题相同：https://leetcode-cn.com/problems/symmetric-tree/

相关标签
树
```

## 题解

### DFS 递归

```JavaScript
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function isSymmetric(root: TreeNode | null): boolean {
    if(root == null) return true;
    // 左子树和右子树互为镜像则为对称树
    return isMirrorTree(root.left,root.right)
};

function isMirrorTree(t1:any,t2:any):boolean {
    // DFS截止条件:
    // 直至遍历完结点都没有截止 则互为镜像
    if(t1 == null && t2 == null) return true;
    // 其中有一结点为null 则不为镜像
    if(t1 == null || t2 == null) return false;

    // 值相等且左右子树互为镜像，则两树为镜像树
    return (t1.val==t2.val) && isMirrorTree(t1.left,t2.right) && isMirrorTree(t1.right,t2.left)
}
```
