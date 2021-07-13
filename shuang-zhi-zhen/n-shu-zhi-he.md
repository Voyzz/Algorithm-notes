# n数之和

两数之和

```javascript
var twoSum = function(nums, target) {
    if(!nums.length) return [];
    let num = nums.slice(0);
    nums.sort((x,y) => x-y);
    let l = 0,r = nums.length-1;
    while(l < r){
        if(nums[l] + nums[r] === target) break;
        else if(nums[l] + nums[r] < target){
            l++;
        }else{
            r--;
        }
    }
    l = num.indexOf(nums[l]);
    r = num.indexOf(nums[r]) === l ? num.indexOf(nums[r],l+1) : num.indexOf(nums[r])
    return [l,r];
};
```

[三数之和](https://leetcode-cn.com/problems/3sum/)

```javascript
var threeSum = function(nums) {
    if(nums.length < 3) return [];
    nums.sort((x,y) => x-y);
    let res = [];
    for(let i = 0;i < nums.length;i++){
        //如果第一个数大于1就没必要排了
        if(nums[i] > 0) return res;
        //去重
        if(i && nums[i] === nums[i-1]) continue;
        let left = i+1,right = nums.length-1;
        while(left < right){
            if(nums[left] + nums[right] + nums[i] === 0){
                res.push([nums[i],nums[left],nums[right]]);
                //去重
                while(left < right && nums[left] === nums[left+1]){
                    left++;
                }
                while(left < right && nums[right] === nums[right-1]){
                    right--;
                }
                left++;
                right--;
            }else if(nums[left] + nums[right] + nums[i] > 0){
                right--;
            }else{
                left++;
            }
        }
    }
    return res;
};
```

最接近的三数之和

```javascript
//思路与前面基本一致，但需要两个变量，一个更新答案，一个更新最小差值
var threeSumClosest = function(nums, target) {
    if(!nums.length) return 0;
    let res = Infinity,mins = Infinity;
    nums.sort((x,y) => x-y);
    for(let i = 0;i < nums.length;i++){
        let left = i + 1,right = nums.length-1;
        while(left < right){
            mins = Math.min(Math.abs(nums[i]+nums[left]+nums[right]-target),mins);
            mins === Math.abs(nums[i]+nums[left]+nums[right]-target) 
            && (res = nums[i]+nums[left]+nums[right]);
            if(nums[i]+nums[left]+nums[right] < target){
                left++;
            }else if(nums[i]+nums[left]+nums[right] > target){
                right--;
            }else{
                break;
            }
        }
    }
    return res;
};
```

