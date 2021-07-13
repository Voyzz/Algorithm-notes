# 出现超过一半的数字

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字

1. count初始化为0，count === 0时，res = 当前数，count++
2. 当前数与res相同count++，否则count--
3. 以上两步能够选出出现次数最多的数，接下来判断它是否超过一半即可

```javascript
function MoreThanHalfNum_Solution(numbers)
{
    let result,count=0;
    for(let i = 0;i < numbers.length;i++){
        if(count === 0){
            result = numbers[i];
            count++;
        }else{
            if(result === numbers[i]){
                count++;
            }else{
                count--;
            }
        }
    }
    let times = numbers.filter(x => x === result).length;
    return times > Math.floor(numbers.length >> 1) ? result : 0;
}
```

