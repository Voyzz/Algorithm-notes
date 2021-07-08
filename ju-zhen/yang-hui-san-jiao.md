# 杨辉三角

```javascript
function print(n) {
    let arr = [],n1 = n;
    while(n1--){
        arr.push([]);
    }
    for(let i = 0;i < n;i++){
        for(let j = 0;j <= i;j++){
            if(j === 0 || j === i) arr[i][j] = 1;
            else{
                arr[i][j] = arr[i-1][j-1]+arr[i-1][j];
            }
        }
    }
    arr.forEach(x => console.log(x.toString().replace(/,/g,' ')));
}
```

