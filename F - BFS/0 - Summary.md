```
* ✨ BFS遍历树
    * 构建一个队列，按照根、左子树、右子树的顺序进入队列
    * 将根节点先入列，每出列一个元素就将其左右子树入列
    * 直至队列为空即为遍历完全


// 计算从起点 start 到终点 target 的最近距离
function BFS(start, target) {
    const queue = [];              // 核心队列
    const visited = new Map();     // 已走路径
    let step = 0;                  // 记录扩散的步数

    queue.push(start);             // 将起点加入队列
    visited.set(start);

    /* 队列不为空则继续遍历 */
    while (queue.length != 0) {
        const sz = queue.length;
        /* 操作这一层的结点 */
        for (int i = 0; i < sz; i++) {
            const cur = queue.shift();

            /* 划重点：这里判断是否到达终点 */
            if (满足条件)
                return step;

            /* 将 cur 的相邻节点加入队列 */
            for (接下来的路径)
                if (!visited.has(x)) {
                    queue.push(x);
                    visited.set(x);
                }
        }

        /* 这一层的结点都操作完了，步数+1 */
        step++;
    }
}

```