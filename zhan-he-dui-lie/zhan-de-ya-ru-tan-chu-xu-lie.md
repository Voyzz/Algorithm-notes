# 栈的压入、弹出序列

## 剑指 Offer 31. 栈的压入、弹出序列

### 题目

```javascript
输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如，序列 {1,2,3,4,5} 是某栈的压栈序列，序列 {4,5,3,2,1} 是该压栈序列对应的一个弹出序列，但 {4,3,5,1,2} 就不可能是该压栈序列的弹出序列。



示例 1：

输入：pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
输出：true
解释：我们可以按以下顺序执行：
push(1), push(2), push(3), push(4), pop() -> 4,
push(5), pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
示例 2：

输入：pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
输出：false
解释：1 不能在 2 之前弹出。


提示：

0 <= pushed.length == popped.length <= 1000
0 <= pushed[i], popped[i] < 1000
pushed 是 popped 的排列。
注意：本题与主站 946 题相同：https://leetcode-cn.com/problems/validate-stack-sequences/
```

### 题解

#### 模拟栈

```javascript
/**
 * @param {number[]} pushed
 * @param {number[]} popped
 * @return {boolean}
 */
var validateStackSequences = function(pushed, popped) {
    let stack = [],
        _p = 0;

    for (const val of pushed){
        stack.push(val)
        while(stack[stack.length-1] == popped[_p] && _p < popped.length){
           stack.pop();
           _p++ 
        }
    }

    return stack.length == 0;
};
```

```javascript
1. 模拟出栈的过程
2. 变量push栈，每次将一个元素压入辅助栈
3. 判断辅助栈是否为空的同时，pop栈的栈顶是否与辅助栈栈顶元素相同，如果都满足则两者出栈
4. 最后判断辅助栈是否为空
// 例如序列1,2,3,4,5是某栈的压入顺序，序列4,5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。
// （注意：这两个序列的长度是相等的）

function IsPopOrder(pushV, popV) {
    let stack = [],k = 0;
    for(let i = 0;i < pushV.length;i++){
        stack.unshift(pushV[i]);
        while(stack[0] && popV[k] && stack[0] === popV[k]){
            stack.shift();
            k++;
        }
    }
    return stack.length === 0;
}
```

