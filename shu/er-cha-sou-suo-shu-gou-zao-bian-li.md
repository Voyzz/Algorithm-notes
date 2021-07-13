# 【二叉搜索树】构造/遍历

```javascript
// 代码构建二叉搜索树
// 二叉搜索树的作用， 对于数据量大的数据，需要找到该数据在不在里面，使用二叉树循环的次数减少，节约性能


let bigNumber = [];
for (let i = 0; i < 1000000; i++){
    bigNumber.push(Math.floor(Math.random() * 1000000))
}

// 判断一个值在不在一个数组里面，

// 代码构建二叉搜索树
function DoubleTreeNode (value){
    this.value = value;
    this.left = null;
    this.right = null;
}


/**
 * 添加一个二叉搜索树的节点
 * @param root
 * @param num
 * @returns {null|boolean}
 */
function addNode(root, num){
    // 如果当前的节点为空，直接返回
    if (!root || root.value === null) return null;
    // 节点的值相同的时候， 返回
    if (root.value === num) return true;
    // 输入的值比节点的值大，放在二叉搜索树的右边
    if (root.value < num){
        // 二叉搜索树的右边值为空，赋值，否在递归
        if (root.right === null) root.right= new DoubleTreeNode(num);
        else addNode(root.right, num)
    }else {
        if (root.left === null) root.left = new DoubleTreeNode(num);
        else addNode(root.left, num);
    }
}


/**
 * 构建二叉搜索树
 * @param list
 * @returns {null|DoubleTreeNode}
 */
function generateDoubleSearchTree(list){
    if (!list || list.length === 0) return null;
    let root = new DoubleTreeNode(list[0]);
    for (let i = 1, l = list.length; i < l; i ++){
        addNode(root, list[i])
    }
    return root;
}
// console.log(bigNumber)
let searchTree = generateDoubleSearchTree(bigNumber);


// 遍历二叉搜索树
/**
 * 通过二叉搜索树来找值是否存在
 * @param treeList
 * @param target
 * @returns {boolean}
 */
let num = 1;
function searchByDoubleTree(treeList, target){
    if (!treeList || treeList.value === null || !target) return false;
    num += 1;
    if (treeList.value === target) return true;
    if (treeList.value > target) return searchByDoubleTree(treeList.left, target);
    else return searchByDoubleTree(treeList.right, target);
}


let num2 = 1;
function searchByArr(list, target){
    for (let i = 0, l = list.length; i < l; i ++){
        num2+=1;
        if (list[i] === target){
            return true;
        }
    }
    return false;
}
console.log(searchByArr(bigNumber, 100000), num2)
console.log(searchByDoubleTree(searchTree, 100000), num);
```

