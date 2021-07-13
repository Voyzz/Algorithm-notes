# 接雨水

```javascript
// 比较巧妙的是如何获取每个单元格所能存放的雨水，可以有以下式子简单表示
// 以左边为例：当前柱子存水量 = 最近最高柱子高度（只看左边到当前柱子） - 当前柱子高度
// 右边同理

function trap(arr){
    if(!arr.length) return 0;
    let left = 0,right = arr.length-1,leftHeight = 0,rightHeight = 0,res = 0;
    while(left < right){
        if(arr[left] < arr[right]){
            leftHeight = Math.max(arr[left],leftHeight);
            res += leftHeight - arr[left];
            left++;
        }else{
            rightHeight = Math.max(arr[right],rightHeight);
            res += rightHeight - arr[right];
            right--;
        }
    }
    return res;
}
```

