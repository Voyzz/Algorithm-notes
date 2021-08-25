# 为运算表达式设计优先级

## LeetCode 241. 为运算表达式设计优先级

[241. 为运算表达式设计优先级](https://leetcode-cn.com/problems/different-ways-to-add-parentheses/)

### 题目

```text
给定一个含有数字和运算符的字符串，为表达式添加括号，改变其运算优先级以求出不同的结果。你需要给出所有可能的组合的结果。有效的运算符号包含 +, - 以及 * 。

示例 1:

输入: "2-1-1"
输出: [0, 2]
解释: 
((2-1)-1) = 0 
(2-(1-1)) = 2
示例 2:

输入: "2*3-4*5"
输出: [-34, -14, -10, -10, 10]
解释: 
(2*(3-(4*5))) = -34 
((2*3)-(4*5)) = -14 
((2*(3-4))*5) = -10 
(2*((3-4)*5)) = -10 
(((2*3)-4)*5) = 10
```

### 题解

#### 分治算法

```javascript
var diffWaysToCompute = function(expression) {
    if(!/\D/g.test(expression)) return [parseInt(expression)];
    const res = [];

    for(let i=0;i<expression.length;i++){
        const _symbol = expression[i];
        // 符号位
        if(["+","-","*"].indexOf(_symbol) > -1){
            const left_res = diffWaysToCompute(expression.slice(0,i));
            const right_res = diffWaysToCompute(expression.slice(i+1));

            for(let l=0;l<left_res.length;l++){
                for(let r=0;r<right_res.length;r++){
                    switch (_symbol){
                        case "+":
                            res.push(left_res[l]+right_res[r]);
                            break;
                        case "-":
                            res.push(left_res[l]-right_res[r]);
                            break;
                        case "*":
                            res.push(left_res[l]*right_res[r]);
                            break;
                    }
                }
            }
        }
    }

    return res;
};
```
