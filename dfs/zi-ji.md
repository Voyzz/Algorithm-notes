# 子集

[子集](https://leetcode-cn.com/problems/subsets/)



给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

1. 定义res数组存储结果
2. 每个子集为状态变量，集合的元素个数为条件变量
3. 子集的元素数量小于等于集合的元素数量为限制条件，满足条件时添加到结果数组，否则回退到上一步
4. 下一层搜索的集合需要去掉已添加到状态变量中的元素

```javascript
var subsets = function(nums) {
    let res = [];
    let n = nums.length;
    function back(path,i){
        if(i <= n){
            res.push(path);
        }
        for(let j = i;j < n;j++){
            path.push(nums[j]);
            back(path.slice(0),j+1);
            path.pop();
        }
    }
    back([],0);
    return res;
};
```

