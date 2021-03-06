# 剑指 Offer 32 - III. 从上到下打印二叉树 III

## 题目

```JavaScript
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

 

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
  [20,9],
  [15,7]
]
 

提示：

节点总数 <= 1000

相关标签
树
广度优先搜索
```

## 题解

### BFS

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

function levelOrder(root: TreeNode | null): number[][] {
    const res:number[][] = [],queue:any[] = [];
    if(!root) return [];
    queue.push(root);

    while(queue.length != 0){
        const level:number[] = [];
        const len = queue.length;
        for(let i=0;i<len;i++){
            const node = queue.shift();
            if(node.left) queue.push(node.left);
            if(node.right) queue.push(node.right);
            if(res.length%2 == 1){
                level.unshift(node.val);
            }else{
                level.push(node.val)
            }
        }
        res.push(level);
    }

    return res;
};
```
