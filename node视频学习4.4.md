###process
####process.argv
```js
var argv = process.argv;

console.log(argv);//前两个参数没有用 都是运行的文件地址！！
```
####process.stdout标准输出
#####process.stdout.write()
```js
console.log = {msg} => {
   process.stdout.write(`${msg}\n`)
 }
 // es6 "=>" 函数的意义
var log = function(message){
    process.stdout.write(message + '\n');
};
// `` 模板字符串,其中可以直接键入回车
var msg = 'hello';
process.stdout.write(`${msg}\n`)
```
#####process.stdout.getWindowSize()
获取高宽
####process.stdin标准输入
#####process.stdin.on()
```js
process.stdin.on('data',(data) => {
    //命令行有回车触发
    process.stdout.write(`data:${data}\n`);
})
```
####Node所有的会发生阻塞的操作都是异步的
#####读取文件

```js
var fs = require('fs');

fs.readFile('文件地址',‘utf8’,(error,data) =>{
    if(error){
     throw error;
     }
     console.log(data);
})
```


