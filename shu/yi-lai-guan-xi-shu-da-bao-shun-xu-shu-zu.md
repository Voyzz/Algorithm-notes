# 【依赖关系树】打包顺序数组

根据js的依赖关系树tree，输出合理的打包顺序的数组

```javascript
function resolve(tree){
    let len = tree.require.length,queue = [];
    for(let i = 0;i < len;i++){
        queue.push([]);
    }
    tree = flatten(tree);
    let head = tree.name;
    for(let key in tree){
        let k = Number(key.slice(8,9));
        Object.keys(tree[key]).length && queue[k].push(tree[key])
    }
    let res = [];
    for(let i = queue.length-1;i >= 0;i--){
        for(let j = queue[i].length-1;j >= 0;j--){
            res.indexOf(queue[i][j]) === -1 && res.push(queue[i][j]);
        }
    }
    return res;
}
function flatten(input) {
    let res = {};
    let re = function(obj,key){
        if(obj instanceof Object && !(obj instanceof Array)){
            let empty = true;
            for(let i in obj){
                re(obj[i],key ? `${key}.${i}` : i)
            }
            if(empty && key){
                res[key] = {};
            }
        }else if(obj instanceof Array){
            if(obj.length){
                for(let i = 0;i < obj.length;i++){
                    re(obj[i],key ? `${key}[${i}]` : i)
                }
            }else{
                res[key] = [];
            }
        }else{
            if(obj !== undefined && obj !== null){
                res[key] = obj;
            }
        }
    };
    re(input,'');
    return res;
}
var tree1 = {
    name: 'main.js',
    require: [{
        name: 'A.js'
    }, {
        name: 'B.js'
    }] }


var tree2 = {
    name: 'page.js',
    require: [{
        name: 'A.js',
        require: [{
            name: 'B.js',
            require: [{
                name: 'C.js'
            }]
        }]},
        {
            name: 'D.js',
            require: [{
                name: 'C.js'
            }, {
                name: 'E.js'
            }]
        }] }
resolve(tree1) // ['A.js', 'B.js', 'main.js']
resolve(tree2) // ['C.js', 'E.js', 'D.js', 'B.js', 'A.js', 'page.js']
```

