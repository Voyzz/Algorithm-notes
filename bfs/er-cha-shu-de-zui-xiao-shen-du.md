# 二叉树的最小深度

## LeetCode 111. 二叉树的最小深度

### 题目

[111](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/)

```text
给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

说明：叶子节点是指没有子节点的节点。



示例 1：


输入：root = [3,9,20,null,null,15,7]
输出：2
示例 2：

输入：root = [2,null,3,null,4,null,5,null,6]
输出：5
```

### 题解

#### BFS

```javascript
var minDepth = function(root) {
    if(root == null) return 0;

    const queue = [];
    let depth = 1;

    queue.push(root);

    while(queue.length !== 0){
        const len = queue.length;
        for(let i=0;i<len;i++){
            const curr = queue.shift();
            if(curr.left == null && curr.right == null){
                return depth;
            }
            if(curr.left) queue.push(curr.left);
            if(curr.right) queue.push(curr.right);
        }
        depth++;
    }
};
```

