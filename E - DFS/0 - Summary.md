```JavaScript
* ✨ DFS、回溯、递归、DP之间的关系
    * 递归就是自我调用，经常作为一种编程的实现方式，比如的DFS 、动态规划、回溯法都可以用递归来实现，当然也可以用非递归来实现。
    * 回溯是一种通用的算法，把问题分步解决，在每一步都试验所有的可能，当发现已经找到一种方式或者目前这种方式不可能是结果的时候，退回上一步继续尝试其他可能。很多时候每一步的处理都是一致的，这时候用递归来实现就很自然。
    * 当回溯用于树的时候，就是DFS。当然了，几乎所有可以用回溯解决的问题都可以表示为树。那么这俩在这里就几乎同义了。如果一个问题解决的时候显式地使用了树，那么我们就叫它dfs。很多时候没有用树我们也管它叫dfs严格地说是不对的，但是dfs比回溯打字的时候好输入。别的回答里提到了砍枝，实际上这二者都可以砍枝。
    * 动态规划。回溯可以用于所有用穷举法可以解决的问题，而DP只用于具有最优子结构的问题。所以不是所有问题都适合用dp来解决，比如八皇后。dp需要存贮子问题的解，回溯不需要。
* ✨ 前中后序遍历
    * 递归/DFS
//前序遍历
const dfs = (root) => {
    if(root){
        console.log(root.val)
        dfs(root.left);
        dfs(root.right)
    }
}
*     ✨ DFS
    
function DFS(){
    //截止条件 (到达最小子叶外)
    if(node != null 或 level < n 或 root.val == n 等){
        // 子节点的逻辑
        DFS(childNode)

        // 如需回溯
        tmp = new_status;
        DFS(new_status);
        statue = tmp;
        
    }
}



```
