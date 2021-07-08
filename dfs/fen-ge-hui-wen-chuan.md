# 分割回文串

[分割回文串](https://leetcode-cn.com/problems/palindrome-partitioning/)



给定一个字符串 s，将 s 分割成一些子串，使每个子串都是回文串。返回 s 所有可能的分割方案。

1. 定义res
2. 状态变量为回文子串集，条件变量为子串集的字符串数目
3. 当子串集的字符串数目与目标串长度相同时，满足要求
4. 下层递归的开始位置由上层递归决定

```javascript
var partition = function(str){
    let res = [];
    function isPalindrome(s){
        let head = 0;
        let tail = s.length-1;
        while(head <= tail){
            if(s[head] !== s[tail]) return false;
            head++;
            tail--;
        }
        return true;
    }
    function backtrack(path,start){
    if(start === str.length) res.push(path);
        for(let i = start;i < str.length;i++){
            if(!isPalindrome(str.slice(start,i+1))) continue;
            path.push(str.slice(start,i+1));
            backtrack(path.slice(),i+1);
            path.pop();
        }
    }
    backtrack([],0);
    return res;
}
```

