# 剑指 Offer 32 - I. 从上到下打印二叉树
## 题目
```
从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

 

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回：

[3,9,20,15,7]
 

提示：

节点总数 <= 1000

相关标签
树
广度优先搜索
```

## 题解
### BFS

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var levelOrder = function(root) {
    if(root == null) return [];

    const res = [],quene = [];
    quene.push(root);
    while(quene.length != 0){
        const node = quene.shift();
        res.push(node.val);
        if(node.left !== null){
            quene.push(node.left);
        }
        if(node.right !== null){
            quene.push(node.right);
        }
    }
    return res;
};
```