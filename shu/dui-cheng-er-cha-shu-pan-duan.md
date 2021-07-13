# 【对称二叉树】判断

[判断二叉树是否是对称二叉树](https://leetcode-cn.com/problems/symmetric-tree/)

```javascript
function mirrors(root){
    if(root === null) return root;
    [root.left,root.right] = [root.right,root.left];
    mirrors(root.left);
    mirrors(root.right);
}
var isSymmetric = function(root) {
    let mirror = JSON.parse(JSON.stringify(root));
    mirrors(mirror);
    if(JSON.stringify(mirror) === JSON.stringify(root)){
        return true;
    }else{
        return false;
    }
};
```

