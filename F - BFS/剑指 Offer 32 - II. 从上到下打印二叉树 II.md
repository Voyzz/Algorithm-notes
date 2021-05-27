# 剑指 Offer 32 - II. 从上到下打印二叉树 II

## 题目

```JavaScript
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

 

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]
 

提示：

节点总数 <= 1000
注意：本题与主站 102 题相同：https://leetcode-cn.com/problems/binary-tree-level-order-traversal/

相关标签
树
广度优先搜索
```

## 题解

### BFS

```JavaScript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[][]}
 */
var levelOrder = function(root) {
    const res = [],queue = [];
    if(root == null) return [];
    queue.push(root);

    while(queue.length != 0){
        // 分层
        const level = [];
        const len = queue.length;
        for(let i=0;i<len;i++){
            const node = queue.shift();
            if(!!node.left) queue.push(node.left);
            if(!!node.right) queue.push(node.right);
            level.push(node.val);
        }
        res.push(level);
    }

    return res;
};
```
