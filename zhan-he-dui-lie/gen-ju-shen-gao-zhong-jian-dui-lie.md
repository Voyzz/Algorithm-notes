# 根据身高重建队列

[根据身高重建队列](https://leetcode-cn.com/problems/queue-reconstruction-by-height/)

假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对\(h, k\)表示，其中h是这个人的身高，k是排在这个人前面且身高大于或等于h的人数。 编写一个算法来重建这个队列。

```javascript
1. 按升高降序，身高相同的按人数升序排列
2. 将队列的每个元素按序插入到索引位置
var reconstructQueue = function(people) {
    if(!people) return [];
    people.sort((x,y)=>{
        return x[0] === y[0] ? x[1]-y[1] : y[0] - x[0];
    });
    let res = [];
    for(let i = 0;i < people.length;i++){
        res.splice(people[i][1],0,people[i]);
    }
    return res;
};

```



