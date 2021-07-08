# 最长上升子数组

[最长上升子序列](https://leetcode-cn.com/problems/longest-increasing-subsequence/)

```javascript
1. 维护一个子序列存放当前的上升序列
2. 将当前数与子序列最大值比较，如果比最大值大之间加入队尾，如果更新则找一个合适的位置替换当前位置的元素

var lengthOfLIS = function(nums) {
    let n = nums.length;
    if(n <= 1){
        return n;
    }
    let tail = [nums[0]];
    for(let i = 0;i < n;i++){
        if(nums[i] > tail[tail.length-1]){
            tail.push(nums[i]);
        }else{
            let left = 0;
            let right = tail.length-1;
            while(left < right){
                let mid = (left + right) >> 1;
                if(tail[mid] < nums[i]){
                    left = mid + 1;
                }else{
                    right = mid;
                }
            }
            tail[left] = nums[i];
        }
    }
    return tail.length;
};
```

