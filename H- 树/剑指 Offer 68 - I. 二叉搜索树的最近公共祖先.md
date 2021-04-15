# 剑指 Offer 68 - I. 二叉搜索树的最近公共祖先
## 题目
```
给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”

例如，给定如下二叉搜索树:  root = [6,2,8,0,4,7,9,null,null,3,5]

![23eabd5bbcca99ebed163bfa851bfb61.png](evernotecid://849303AB-DE4A-407B-BB36-67ADB0B253A4/appyinxiangcom/24827522/ENResource/p338)

示例 1:

输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
输出: 6 
解释: 节点 2 和节点 8 的最近公共祖先是 6。
示例 2:

输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
输出: 2
解释: 节点 2 和节点 4 的最近公共祖先是 2, 因为根据定义最近公共祖先节点可以为节点本身。
 

说明:

所有节点的值都是唯一的。
p、q 为不同节点且均存在于给定的二叉搜索树中。
注意：本题与主站 235 题相同：https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-search-tree/

相关标签
树
```

## 题解
### 
```
var lowestCommonAncestor = function(root, p, q) {
    while(true){
        // 根节点的值比两个点的值都大：两个点都在其左子树
        if(root.val > p.val && root.val > q.val) root = root.left;
        // 根节点的值比两个点的值都小：两个点都在其右子树
        else if(root.val < p.val && root.val < q.val) root = root.right;
        // 一大一小或有相等则说明是公共结点
        else return root;
    }
};
```