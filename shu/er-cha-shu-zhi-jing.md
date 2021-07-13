# 【二叉树】直径

一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过也可能不穿过根结点。

```javascript
易错点是直径可能不经过根节点
用max保存最大值，
当每个节点作为根节点时，与max比较进行更新

var diameterOfBinaryTree = function(root) {
    let max = 0;
    function dfs(root){
        if(!root) return 0;
        let l = dfs(root.left);
        let r = dfs(root.right);
        max = Math.max(max,l+r);
        return Math.max(l,r)+1;
    }
    dfs(root);
    return max;
};
```

