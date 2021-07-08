# 计算后缀表达式

```javascript
1. 数字入栈
2. 运算符，栈顶作为右操作数，次栈顶作为左操作数
3. 将运算结果入栈
4. 栈最后一个值即为结果

function CalcRPN(str) {
    let stack = [];
    let num = '';
    for(let i = 0;i < str.length;i++){
        if(str[i] === ' '){
            if(num !== '') stack.push(Number(num));
            num = '';
        }else if(!Object.is(Number(str[i]),NaN)){
            num += str[i];
        }else if(str[i] === '+'){
            let right = stack.pop();
            let left = stack.pop();


            stack.push(left + right);
        }else if(str[i] === '-'){
            let right = stack.pop();
            let left = stack.pop();
            stack.push(left - right);
        }else if(str[i] === '*'){
            let right = stack.pop();
            let left = stack.pop();
            stack.push(left * right);
        }else if(str[i] === '/'){
            let right = stack.pop();
            let left = stack.pop();
            stack.push(left / right);
        }
    }
    return stack.pop();
}
```

