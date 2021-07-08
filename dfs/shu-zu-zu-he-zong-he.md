# 数组组合总和

[组合总和](https://leetcode-cn.com/problems/combination-sum/)



给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。candidates 中的数字可以无限制重复被选取。

1. 定义res
2. 每个子数组为状态变量，目标值为条件变量
3. 子数组中的值相加等于目标值则满足要求
4. 下一层递归的tar（与目标值相差的数目）依赖于上一层递归的选择

```javascript
var combinationSum = function(candidates, target) {
    let res = [];
    let len = candidates.length;
    //这里排序是为了防止在for循环if判断时直接跳出了，比如这样的样例[8,7,4,3],11
    candidates.sort((x,y) => x-y);    
    function back(path,i,tar){
        if(tar === 0){
            res.push(path);
            return;
        }
        for(let j = i;j < len;j++){
            //判断是否当前的路口都是通向死路
            if(tar < candidates[j]) break;          
            path.push(candidates[j]);
            back(path.slice(),j,tar-candidates[j]);
            path.pop();
        }
    }
    back([],0,target);
 
    return res;
};
```

