# 【二叉树】深度

## 剑指 Offer 55 - I. 二叉树的深度

### 题目

```text
输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

例如：

给定二叉树 [3,9,20,null,null,15,7]，

    3
   / \
  9  20
    /  \
   15   7
返回它的最大深度 3 。



提示：

节点总数 <= 10000
注意：本题与主站 104 题相同：https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/

相关标签
树
深度优先搜索
```

### 题解

#### DFS

```javascript
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

function maxDepth(root: TreeNode | null): number {
    let maxDep:number = 0;

    // 后序遍历搜索树
    function dfs(node:any,level:number):void{
        if(!!node){
            maxDep = Math.max(level,maxDep);
            dfs(node.left,level+1);
            dfs(node.right,level+1);
        }
    }

    dfs(root,1);
    return maxDep;
};
```

#### 递归

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var maxDepth = function(root) {
    if(root == null) return 0;
    return Math.max(maxDepth(root.left),maxDepth(root.right))+1
};
```

