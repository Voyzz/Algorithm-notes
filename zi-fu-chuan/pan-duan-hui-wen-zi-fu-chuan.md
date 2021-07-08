# 判断回文字符串

```javascript
var isPalindrome = function(s) {
    let reg = /[a-z]|[0-9]/;
    s = s.split('').map(x => x.toLowerCase()).filter((x) => reg.test(x)).join('');
    let head = 0;
    let tail = s.length-1;
    while(head <= tail){
        if(s[head] !== s[tail]) return false;
        head++;
        tail--;
    }
    return true;
};
```

