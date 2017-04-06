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






