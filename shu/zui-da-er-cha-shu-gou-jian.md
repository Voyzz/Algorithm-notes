# 【最大二叉树】构建

## LeetCode 654. 最大二叉树

### 题目

```text
给定一个不含重复元素的整数数组 nums 。一个以此数组直接递归构建的 最大二叉树 定义如下：

二叉树的根是数组 nums 中的最大元素。
左子树是通过数组中 最大值左边部分 递归构造出的最大二叉树。
右子树是通过数组中 最大值右边部分 递归构造出的最大二叉树。
返回有给定数组 nums 构建的 最大二叉树 。

输入：nums = [3,2,1,6,0,5]
输出：[6,3,5,null,2,0,null,null,1]
解释：递归调用如下所示：
- [3,2,1,6,0,5] 中的最大值是 6 ，左边部分是 [3,2,1] ，右边部分是 [0,5] 。
    - [3,2,1] 中的最大值是 3 ，左边部分是 [] ，右边部分是 [2,1] 。
        - 空数组，无子节点。
        - [2,1] 中的最大值是 2 ，左边部分是 [] ，右边部分是 [1] 。
            - 空数组，无子节点。
            - 只有一个元素，所以子节点是一个值为 1 的节点。
    - [0,5] 中的最大值是 5 ，左边部分是 [0] ，右边部分是 [] 。
        - 只有一个元素，所以子节点是一个值为 0 的节点。
        - 空数组，无子节点。
示例 2：


输入：nums = [3,2,1]
输出：[3,null,2,null,1]
```

### 题解

#### 递归

```javascript
var constructMaximumBinaryTree = function(nums) {
    // 函数意义：构造出以nums中最大值为根节点的最大二叉树
    // root结点要做什么：构造最大二叉树

    // [base case] 数组为空，停止操作
    if(nums.length == 0) return null;

    // [前序遍历][根节点操作] 找出最大值，坐标；构造根节点
    let max,max_i;
    for(let i=0;i<nums.length;i++){
        if(!max || nums[i] > max){
            max = nums[i];
            max_i = i;
        }
    }
    let left_nums = nums.slice(0,max_i),
        right_nums = nums.slice(max_i+1);
    let root = new TreeNode(max);

    // 遍历子数组
    root.left = constructMaximumBinaryTree(left_nums);
    root.right = constructMaximumBinaryTree(right_nums);

    // 返回root
    return root;
};
```

