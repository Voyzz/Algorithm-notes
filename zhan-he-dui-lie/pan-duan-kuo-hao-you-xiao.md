# 判断括号有效

## [LeetCode 20. 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

### 题目

```javascript
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
```

### 题解

#### 辅助栈

```javascript
// 左括号入栈，右括号与栈顶比较是否匹配，匹配弹出栈顶，不匹配return false
// 查看栈是否为空
var isValid = (s) => {
  const map = { "{": "}", "(": ")", "[": "]" }
  const stack = []
  for (let i = 0; i < s.length; i++) {
    const cur = s[i]
    if (map[cur]) {
      stack.push(cur)
    } else {
      if (stack.length === 0) {
        return false
      }
      const stackTop = stack.pop()
      if (map[stackTop] !== cur) {
        return false
      }
    }
  }
  return stack.length === 0
}
```

