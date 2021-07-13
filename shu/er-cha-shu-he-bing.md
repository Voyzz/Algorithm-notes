# 【二叉树】合并

[合并二叉树](https://leetcode-cn.com/problems/merge-two-binary-trees/)

```javascript
var mergeTrees = function(t1, t2) {
    if(t1 && t2){
        t1.val += t2.val;
        t1.left = mergeTrees(t1.left,t2.left);
        t1.right = mergeTrees(t1.right,t2.right);
    }
    return t1 || t2;
};
```

