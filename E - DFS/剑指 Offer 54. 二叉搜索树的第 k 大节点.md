# 剑指 Offer 54. 二叉搜索树的第 k 大节点

## 题目

```JavaScript
给定一棵二叉搜索树，请找出其中第k大的节点。

 

示例 1:

输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
示例 2:

输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
 

限制：

1 ≤ k ≤ 二叉搜索树元素个数

相关标签
树
```

## 题解

###

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

function kthLargest(root: TreeNode | null, k: number): number {
    let count:number = 0,res:number;
    
    // 后序遍历搜索树 得到的结点值是递减的
    function dfs(node:any):void{
        if(node){
            dfs(node.right);
            if(++count == k){
                res = node.val;
                return
            }
            dfs(node.left);
        }
    }

    dfs(root);
    return res;
};
```
