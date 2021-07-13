# 【二叉搜索树】判断后序遍历

```javascript
1. 后序遍历的最后一个节点为根节点
2. 二叉索引树右子树大于根节点，左子树小于根节点，所以可以用根节点将树分为两颗子树
3. 二叉索引树的子树也是二叉索引树，所以分别对子树进行判断，直到遍历到最后一个节点

var verifyPostorder = function(postorder) {
    if(!postorder.length) return true;
    let tail = postorder.pop();
    let key = postorder.length;
    for(let i = 0;i < postorder.length;i++){
        if(postorder[i] > tail){
            key = i;
            break;
        }
    }
    for(let i = key+1;i < postorder.length;i++){
        if(postorder[i] < tail){
            return false;
        }
    }
    return verifyPostorder(postorder.slice(0));
};

```

