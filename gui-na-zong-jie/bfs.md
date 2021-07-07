# BFS

## 思想

* 把一些问题抽象成图，从一个点开始，向四周开始扩散。
* 本质上就是一幅「图」，让你从一个起点，走到终点，问最短路径
*  BFS 算法都是用**队列**这种数据结构，每次将一个节点周围的所有节点加入队列。
* BFS 找到的路径一定是最短的，但代价就是空间复杂度比 DFS 大很多
* **空间复杂度**O\(n\)

## 框架

```javascript
var levelOrder = function(root) {
    if(root == null) return [];

    const res = [],quene = [];
    quene.push(root);
    while(quene.length != 0){
        const node = quene.shift();
        
        // 当前节点处理逻辑在这里
        res.push(node.val);
        
        if(node.left !== null){
            quene.push(node.left);
        }
        if(node.right !== null){
            quene.push(node.right);
        }
    }
    return res;
};
```

