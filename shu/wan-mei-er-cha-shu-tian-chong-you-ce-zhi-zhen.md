# 【完美二叉树】填充右侧指针

## LeetCode 116. 填充每个节点的下一个右侧节点指针

### 题目

```text
给定一个 完美二叉树 ，其所有叶子节点都在同一层，每个父节点都有两个子节点。二叉树定义如下：

struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。

初始状态下，所有 next 指针都被设置为 NULL。
```

### 题解

#### 递归

```javascript
var connect = function(root) {
    if(root == null) return null;
    connectTwoNodes(root.left,root.right);
    return root;
};

const connectTwoNodes = function(node1,node2){
    if(!node1 || !node2) return;

    node1.next = node2;

    connectTwoNodes(node1.left,node1.right);
    connectTwoNodes(node1.right,node2.left);
    connectTwoNodes(node2.left,node2.right);
}
```

