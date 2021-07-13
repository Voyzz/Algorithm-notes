# 【二叉树】重复的子树

## LeetCode 652. 寻找重复的子树

### 题目

```text
给定一棵二叉树，返回所有重复的子树。对于同一类的重复子树，你只需要返回其中任意一棵的根结点即可。

两棵树重复是指它们具有相同的结构以及相同的结点值。

示例 1：

        1
       / \
      2   3
     /   / \
    4   2   4
       /
      4
下面是两个重复的子树：

      2
     /
    4
和

    4
因此，你需要以列表的形式返回上述重复子树的根结点。
```

### 题解

#### 递归

```javascript
var findDuplicateSubtrees = function(root) {
    const res = [];
    const hash = new Map();

    function traverse(root){
        if(root == null) return '#';

        let left_tree_str = traverse(root.left),
            right_tree_str = traverse(root.right),
            tree_str = left_tree_str+","+right_tree_str+","+root.val;

        if(hash.get(tree_str)){
            hash.set(tree_str,hash.get(tree_str)+1)
        }else{
            hash.set(tree_str,1);
        }
        if(hash.get(tree_str) === 2){
            res.push(root);
        }

        return tree_str;

    }

    traverse(root);
    return res;
};
```

