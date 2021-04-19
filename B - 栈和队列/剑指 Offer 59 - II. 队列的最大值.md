# 剑指 Offer 59 - II. 队列的最大值

## 题目

```JavaScript
请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1

示例 1：

输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
示例 2：

输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
 

限制：

1 <= push_back,pop_front,max_value的总操作数 <= 10000
1 <= value <= 10^5

相关标签
栈
Sliding Window
```

## 题解

### 辅助队列

```JavaScript
var MaxQueue = function() {
    this.quene1 = [];
    this.quene2 = [];
};

/**
 * @return {number}
 */
MaxQueue.prototype.max_value = function() {
    return this.quene2.length>0 ? this.quene2[0] : -1;
};

/** 
 * @param {number} value
 * @return {void}
 */
MaxQueue.prototype.push_back = function(value) {
    this.quene1.push(value);
    // pop出比value小的，构造递减队列
    while(this.quene2.length > 0 && this.quene2[this.quene2.length-1] < value){
        this.quene2.pop();
    }
    this.quene2.push(value);
};

/**
 * @return {number}
 */
MaxQueue.prototype.pop_front = function() {
    const head = this.quene1.length>0 ? this.quene1.shift() : -1;
    if(this.quene2.length>0 && head == this.quene2[0]){
        this.quene2.shift()
    }
    return head
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * var obj = new MaxQueue()
 * var param_1 = obj.max_value()
 * obj.push_back(value)
 * var param_3 = obj.pop_front()
 */
```
