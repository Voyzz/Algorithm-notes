# 盛最多水的容器

```javascript
//双指针时刻更新最大值即可,实质上还是枚举
var maxArea = function(height) {
    if(!height.length) return 0;
    let left = 0,right = height.length-1,res = 0;
    while(left < right){
        if(height[left] <= height[right]){
            let cur = height[left] * (right - left);
            res = Math.max(res,cur);
            left++;
        }else{
            let cur = height[right] * (right - left);
            res = Math.max(res,cur);
            right--;
        }
    }
    return res;
};
```

