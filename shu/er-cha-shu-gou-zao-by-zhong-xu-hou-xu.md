# 【二叉树】构造by中序后序

## LeetCode 106. 从中序与后序遍历序列构造二叉树

### 题目

```text
根据一棵树的中序遍历与后序遍历构造二叉树。

注意:
你可以假设树中没有重复的元素。

例如，给出

中序遍历 inorder = [9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7
```

### 题解

#### 递归

```javascript
var buildTree = function(inorder, postorder) {
    if(inorder.length === 0) return null;

    let root_val = postorder[postorder.length-1],
        root_index_inorder = inorder.indexOf(root_val),
        root = new TreeNode(root_val);

    let inorder_left = inorder.slice(0,root_index_inorder),
        inorder_right = inorder.slice(root_index_inorder+1),
        postorder_left = postorder.slice(0,inorder_left.length),
        postorder_right = postorder.slice(inorder_left.length,-1);

    root.left = buildTree(inorder_left,postorder_left);
    root.right = buildTree(inorder_right,postorder_right);

    return root;
};
```

