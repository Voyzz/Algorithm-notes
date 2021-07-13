# 【二叉树】前中后序遍历

```javascript
//递归
function pre(root){
    if(!root) return root;
    console.log(root.val);
    pre(root.left);
    pre(root.right);
}


function mid(root){
    if(!root) return root;
    mid(root.left);
    console.log(root.val);
    mid(root.right);
}


function next(root){
    if(!root) return root;
    next(root.right);
    next(root.left);
    console.log(root.val);
}


//非递归
//前序
//用栈进行模拟
//每次将栈顶元素添加到结果中，然后将栈顶元素的左右非空子树入栈（注意右子树先入栈，后弹出）
//直到栈为空跳出循环

function pre(root){
    if(root === null) return root;
    let res = [],stack = [];
    stack.push(root);
    while (stack.length){
        let node = stack.pop();
        res.push(node.val);
        node.right && stack.push(node.right);
        node.left && stack.push(node.left);
    }
    return res;
}


//中序
//对栈顶元素深度遍历左子树入栈，然后将栈顶添加到结果中，然后访问当前子节点的右子树，依次循环
function mid(root){
    if(root === null) return root;
    let res = [],stack = [];
    stack.push(root);
    while (stack.length){
        while(root !== null){
            stack.push(root);
            root = root.left;
        }
        let node = stack.pop()
        res.push(node.val);
        root = node.right;
    }
    //根节点添加了两次
    return res.slice(0,res.length-1);
}


//后序
//与前序相似，但生成顺序为根右左，最后将res反序
function next(root){
    if(root === null) return root;
    let res = [],stack = [];
    stack.push(root);
    while (stack.length){
        let node = stack.pop();
        res.push(node.val);
        node.left && stack.push(node.left);
        node.right && stack.push(node.right);
    }
    return res.reverse();
}
```



