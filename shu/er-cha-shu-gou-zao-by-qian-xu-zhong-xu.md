# 【二叉树】构造by前序中序

[从前序与中序遍历序列构造二叉树](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

```javascript
var buildTree = function(preorder, inorder) {
    if(!preorder.length || !inorder.length) return null;
    let root = new TreeNode(preorder[0]);
    let key = 0;
    for(let i = 0;i < inorder.length;i++){
        if(inorder[i] === preorder[0]){
            key = i;
            break;
        }
    }
    root.left = buildTree(preorder.slice(1,key+1),inorder.slice(0,key));
    root.right = buildTree(preorder.slice(key+1),inorder.slice(key+1));
    return root;
};
```

