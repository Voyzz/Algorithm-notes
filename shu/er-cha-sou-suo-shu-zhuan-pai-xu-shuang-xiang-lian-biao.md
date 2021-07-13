# 【二叉搜索树】转排序双向链表

```javascript
var treeToDoublyList = function(root) {
    if(!root) return null;
    let head = null,tail = null,pre = null;
    function dfs(root){
        if(!root) return null;
        dfs(root.left);
        //第一个节点作为头节点
        if(!pre) head = root;
        //将上一个节点的后继指针指向当前节点
        else pre.right = root;
        //将当前指针的前驱指针指向上一个节点
        root.left = pre;
        //更新上一个节点
        pre = root; 
        //更新尾部节点
        tail = root;
        dfs(root.right);
    }
    dfs(root);
    //首尾连接
    head.left = tail;
    tail.right = head;
    return head;
};
```

