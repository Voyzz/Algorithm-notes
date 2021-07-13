# 旋转数组的最小元素

输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素



1. 原数据为旋转数组，所以分界点前后都是有序的
2. 进行二分查找，注意因为找最小值，high赋值时应该从mid开始取，mid可能是最小值

```javascript
function minNumberInRotateArray(rotateArray)
{
    if(!rotateArray.length) return 0;
    let left = 0,right = rotateArray.length-1;
    while(left < right){
        let mid = Math.floor((right+left) >> 1);
        if(rotateArray[left] <= rotateArray[right]){
            return rotateArray[left];
        }
        if(rotateArray[left] < rotateArray[mid]){
            left = mid + 1;
        }else if(rotateArray[right] > rotateArray[mid]){
            right = mid;
        }else{
            left++;
        }
    }
}
```

