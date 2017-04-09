###异步操作
####进程包含线程，V8引擎最大特点就是单线程操作。进程指进行中的程序。
###实现命令行计算器
* 1 接收参数

```javascript
const args = process.argv.slice(2);
```
* 2 分析参数

```js
let parameter1 = args[0];
let operator = args[1];
let parameter2 = args[2];
```
* 3进行运算

```js
//let result = eval(`${parameter1} ${operator} ${parameter2}`);
//console.log(result);

switch (operator) {
    case '+':
        result = parseFloat(parameter1) + parseFloat(parameter2); 
        break;
    case '-':
        result = parseFloat(parameter1) - parseFloat(parameter2); 
        break;
    case '×':
    case '*':
        result = parseFloat(parameter1) * parseFloat(parameter2); 
        break;
    case '/':
    case '÷':
        result = parseFloat(parameter1) / parseFloat(parameter2); 
        break;

    default:
    throw new Error("不支持");
}
console.log(result);
```
* 4删除模块缓存

#####一般不主动删除缓存，因为加载文件是阻塞操作，影响效率。但在类如json数据或者需要重新加载。

#####删除缓存

```js
object.keys(require.cache).forEach((key) => {
    delete require.cache[]
});
```
#####实现缓存
```js
$require.cache = $require.cache||{};
if ($require.cache[filename]){
return $require.cache[filename].exports;
}
···//代码执行段
$require.cache[filename] = module;//将module缓存起来
```





