# 不重复字母构成字符串

## 不重复字母构成字符串

### 题目

```text
输入:['a','b'.'c']
输出:["abc", "acb", "bac", "bca", "cab", "cba"]
```

### 题解

#### DFS 递归

```javascript
function test(test_arr){
    const res = []

    function dfs(arr,str) {
        if(arr.length >= str.length){
            if(arr.length == str.length) res.push(str);

            for (var i = 0; i < arr.length; i++) {
                const tmp = arr[i]
                if(!!tmp){
                    const tmp_str = str;
                    str += arr[i];
                    arr[i] = NaN;
                    dfs(arr,str);
                    str = tmp_str;
                    arr[i] = tmp;
                }
            }
        }
    };

    dfs(test_arr,"")
    return res;
}

function test(test_arr) {
    const res = [],
        str_len = test_arr.length;

    function dfs(curr_str,curr_arr){
        if(curr_str.length === str_len){
            res.push(curr_str);
            return;
        }
        const len = curr_arr.length;
        for(let i=0;i<len;i++){
            const tmp = curr_arr.splice(i,1);
            dfs(curr_str+tmp,curr_arr);
            curr_arr.splice(i,0,tmp[0]);
        }
    }

    dfs("",test_arr)
    return res;
}
```

