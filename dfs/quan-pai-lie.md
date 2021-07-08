# 全排列

[全排列](https://leetcode-cn.com/problems/permutations/)



给定一个 没有重复 数字的序列，返回其所有可能的全排列。

1. 定义res
2. 每个排列序列为状态变量，排列序列中集合的个数为条件变量
3. 当排列序列的元素个数等于给定序列时，满足条件
4. 下一层递归依赖于上一层递归传递的路径

```javascript
var permute = function(nums) {
    let len = nums.length;
    let res = [];
    
    function back(path){
        if(path.length === len){
            res.push(path);
            return;
        }
        for(let i = 0;i < len;i++){
            if(path.indexOf(nums[i]) === -1){    //这里的判断很精髓
                path.push(nums[i]);
                back(path.slice());
                path.pop();
            }
        }
    }
    back([]);
    return res;
};
```

