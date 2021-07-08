# 定义栈数据结构

```javascript
1. 使用辅助栈存最小值
2. 入栈时检查元素是否为最小值，若是则压入主栈和辅助栈
3. 出栈时检查主栈栈顶元素是否与辅助栈一致，若是则一起弹出
// 注意：保证测试中不会当栈为空的时候，对栈调用pop()或者min()或者top()方法。

let stack1 = [],stack2 = [];
function push(value) {
    if(value <= Math.min(...stack1) || stack1.length === 0){
        stack1.unshift(value);
        stack2.unshift(value);
    }else{
        stack1.unshift(value)
    }
}


function pop() {
    if(stack1.length > 0) {
        if (stack1[0] === stack2[0]) {
            stack1.shift();
            stack2.shift();
        } else {
            stack1.shift();
        }
    }
}


function top() {
    if(stack1.length > 0) {
        return stack1[0];
    }
}


function min() {
    if(stack2.length > 0) {
        return stack2[0];
    }
}
```

