# 中缀转后缀

```javascript
//数字直接添加到result
//栈空，运算符直接入栈
//遇到左括号直接入栈，遇到右括号栈顶元素添加到result中然后弹栈，依次循环直到遇到左括号，然后将左括号弹栈
//遇到运算符，判断运算符与栈顶元素的优先级，将所有优先级大于等于该运算符的栈顶弹栈，然后入栈该运算符
//将栈中剩余的字符添加到result中

function toPoland(str){
    let stack = [],result = '';
    for(let i = 0;i < str.length;i++){
        if(!Object.is(Number(str[i]),NaN)){
            result += str[i];
        }else if(stack.length === 0 && Object.is(Number(str[i]),NaN)){
            result += ' ';
            stack.push(str[i]);
        }else if(str[i] === '('){
            stack.push(str[i])
        }else if(str[i] === ')'){
            result += ' ';
            while(stack[stack.length-1] !== '('){
                result += stack.pop();
            }
            stack.pop();
        }else if(str[i] === '*' || str[i] === '/'){
            while(stack[stack.length-1] === '*' || stack[stack.length-1] === '/'){
                result += ' ' + stack.pop();
            }
            result += ' ';
            stack.push(str[i]);
        }else if(str[i] === '+' || str[i] === '-'){
            while(stack[stack.length-1] === '*' || stack[stack.length-1] === '/' || stack[stack.length-1] === '+' || stack[stack.length-1] === '-'){
                result += ' ' + stack.pop();
            }
            result += ' ';
            stack.push(str[i]);
        }
    }
    while(stack.length){
        result += ' ' + stack.pop();
    }
    return result;
}
```

