# 【红黑树】构造

红黑树\(Red-Black Tree 「RBT」\)：自平衡\(不是绝对的平衡\)的二叉查找树\(BST\)。

* 规则:

1. 树的根始终是黑色的 \(黑土地孕育黑树根\)

1. 2. 没有两个相邻的红色节点（红色节点不能有红色父节点或红色子节点，并没有说不能出现连续的黑色节点）
2. 3. 从节点（包括根）到其任何后代NULL节点\(叶子结点下方挂的两个空节点，并且认为他们是黑色的\)的每条路径都具有相同数量的黑色节点

* 作用：

红黑树是一种自平衡二叉树，查找时算法时间复杂度为O\(log n\)。

```javascript
let btins = new RBT();
let ary = [5, 3, 6, 8, 4, 2];


ary.forEach(value => btins.add(value));
btins.generateDepthString1();
// ///////////////
//      5       //
//    /   \     //
//   3     8    //
//  / \   /     //
// 2  4  6      //
// ///////////////
console.log(btins.minmun());  // 2
console.log(btins.maximum()); // 8
```

```javascript
const RED = true;
const BLACK = false;
class Node {
    constructor(key, value) {
        this.key = key;
        this.value = value;
        this.left = null;
        this.right = null;
        this.color = RED;
    }
}
```

```javascript
class RBT {
    constructor() {
        this.root = null;
        this.size = 0;
    }
    isRed(node) {
        if (!node) return BLACK;
        return node.color;
    }
    // 左旋 右红左黑
    leftRotate(node) {
        let tmp = node.right;
        node.right = tmp.left;
        tmp.left = node;
        tmp.color = node.color;
        node.color = RED;
        return tmp;
    }
    // 右旋转 左红左子红
    rightRoate(node) {
        let tmp = node.left;
        node.left = tmp.right;
        tmp.right = node;
        tmp.color = node.color;
        node.color = RED;
        return tmp;
    }
    // 颜色翻转
    flipColors(node) {
        node.color = RED;
        node.left.color = BLACK;
        node.right.color = BLACK;
    }
    add(key, value) {
        this.root = this.addRoot(this.root, key, value);
        this.root.color = BLACK; // 根节点始终是黑色
    }
    addRoot(node, key, value) {
        if (!node) {
            this.size++;
            return new Node(key, value);
        }
        if (key < node.key) {
            node.left = this.addRoot(node.left, key, value);
        } else if (key > node.key) {
            node.right = this.addRoot(node.right, key, value);
        } else {
            node.value = value;
        }
        if (this.isRed(node.right) && !this.isRed((node.left))) {
            node = this.leftRotate(node);
        }
        if (this.isRed(node.left) && this.isRed((node.left.left))) {
            node = this.rightRoate(node);
        }
        if (this.isRed(node.left) && this.isRed(node.right)) {
            this.flipColors(node);
        }
        return node;
    }
    isEmpty() {
        return this.size == 0 ? true : false;
    }
    getSize() {
        return this.size;
    }
    contains(key) {
        let ans = '';
        !(function getNode(node, key) {
            if (!node || key == node.key) {
                ans = node;
                return node;
            } else if (key > node.key) {
                return getNode(node.right, key);
            } else {
                return getNode(node.right, key);
            }
        })(this.root, key);
        return !!ans;
    }
    // bst前序遍历(递归版本)
    preOrder(node = this.root) {
        if (node == null) return;
        console.log(node.key);
        this.preOrder(node.left);
        this.preOrder(node.right);
    }
    preOrderNR() {
        if (this.root == null) return;
        let stack = [];
        stack.push(this.root);
        while (stack.length > 0) {
            let curNode = stack.pop();
            console.log(curNode.key);
            if (curNode.right != null) stack.push(curNode.right);
            if (curNode.left != null) curNode.push(curNode.left);
        }
    }
    // bst中序遍历
    inOrder(node = this.root) {
        if (node == null) return;
        this.inOrder(node.left);
        console.log(node.key);
        this.inOrder(node.right);
    }
    // bst后续遍历
    postOrder(node = this.root) {
        if (node == null) return;
        this.postOrder(node.left);
        this.postOrder(node.right);
        console.log(node.key);
    }
    // bsf + 队列的方式实现层次遍历
    generateDepthString1() {
        let queue = [];
        queue.unshift(this.root);
        while (queue.length > 0) {
            let tmpqueue = []; let ans = [];
            queue.forEach(item => {
                ans.push(item.key);
                item.left ? tmpqueue.push(item.left) : '';
                item.right ? tmpqueue.push(item.right) : '';
            });
            console.log(...ans);
            queue = tmpqueue;
        }
    }
    minmun(node = this.root) {
        if (node.left == null) return node;
        return this.minmun(node.left);
    }
    maximum(node = this.root) {
        if (node.right == null) return node;
        return this.maximum(node.right);
    }
}
```

