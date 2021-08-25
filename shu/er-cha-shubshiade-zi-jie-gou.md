# 【二叉树】B是A的子结构

## 剑指 Offer 26. 树的子结构

### 题目

```text
输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

例如:
给定的树 A:

     3
    / \
   4   5
  / \
 1   2
给定的树 B：

   4 
  /
 1
返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。

示例 1：

输入：A = [1,2,3], B = [3,1]
输出：false
示例 2：

输入：A = [3,4,5,1,2], B = [4,1]
输出：true
限制：

0 <= 节点个数 <= 10000

相关标签
树
```

### 题解

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
 * @param {TreeNode} A
 * @param {TreeNode} B
 * @return {boolean}
 */
var isSubStructure = function(A, B) {
    if(B == null || A == null) return false;
    return isInClude(A,B) || isSubStructure(A.left,B) || isSubStructure(A.right,B);
};

// A是否包含B
const isInClude = function(A,B){
    if(B == null) return true;
    if(A == null) return false;
    if(A.val != B.val) return false;
    return isInClude(A.left,B.left) && isInClude(A.right,B.right);
}
```
