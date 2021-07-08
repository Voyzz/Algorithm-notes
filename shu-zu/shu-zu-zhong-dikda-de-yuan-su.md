# 数组中第k大的元素

[数组中的第K个最大元素](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

```javascript
// 优先队列
var findKthLargest = function(nums, k) {
    let queue = [];
    for(let i = 0;i < nums.length;i++){
        if(queue.length < k) {
           let pos = 0;
           while(pos < k) {
               if(queue[pos] === undefined) {
                    queue[pos] = nums[i];
                    break;
               } else {
                   if(nums[i] > queue[pos]) {
                       queue.splice(pos,0,nums[i]);
                       break;
                   }
               }
               pos++;
           }
        } else {
            if(nums[i] > queue[k-1]) {
                let pos = 0;
                while(pos < k) {
                    if(nums[i] > queue[pos]) {
                       queue.splice(pos,0,nums[i]);
                       queue.pop();
                       break;
                    }
                    pos++;
                }                
            }
        }
    }
    return queue[k-1];
};

```

