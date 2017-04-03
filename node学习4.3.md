
###1、阻塞与非阻塞
阻塞是按顺序执行的，而非阻塞是不需要按顺序的，所以如果需要处理回调函数的参数，我们就需要写在回调函数内。
如：非阻塞

```js
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
    if (err) return console.error(err);//回调函数
    console.log(data.toString());
});

console.log("程序执行结束!");
```
###2、事件循环
####事件驱动
```js
// 引入 events 模块
var events = require('events');

// 创建 eventEmitter 对象
var eventEmitter = new events.EventEmitter();

// 绑定事件及事件的处理程序
eventEmitter.on('eventName', eventHandler);

// 触发事件
eventEmitter.emit('eventName');
```
####node工作进程
在 Node 应用程序中，执行异步操作的函数将回调函数作为最后一个参数， 回调函数接收错误对象作为第一个参数。

###3、EventEmitter
EventEmitter 的每个事件由一个事件名和若干个参数组成，事件名是一个字符串，通常表达一定的语义。对于每个事件，EventEmitter 支持 若干个事件监听器。
当事件触发时，注册到这个事件的事件监听器被依次调用，事件参数作为回调函数参数传递。
####demo
```js
//event.js 文件
var EventEmitter = require('events').EventEmitter; 
var event = new EventEmitter(); 
event.on('some_event', function() { 
	console.log('some_event 事件触发'); 
}); 
setTimeout(function() { 
	event.emit('some_event'); 
}, 1000); 
```
####属性
EventEmitter 提供了多个属性，如 on 和 emit。on 函数用于绑定事件函数，emit 属性用于触发一个事件。接下来我们来具体看下 EventEmitter 的属性介绍。

- 1	addListener(event, listener)
为指定事件添加一个监听器到监听器数组的尾部。

- 2	on(event, listener)
为指定事件注册一个监听器，接受一个字符串 event 和一个回调函数。
> `
server.on('connection', function (stream) {
  console.log('someone connected!');
});
`

- 3	once(event, listener)
为指定事件注册一个单次监听器，即 监听器最多只会触发一次，触发后立刻解除该监听器。
> `
server.once('connection', function (stream) {
  console.log('Ah, we have our first user!');
});
`

- 4	removeListener(event, listener)
移除指定事件的某个监听器，监听器 必须是该事件已经注册过的监听器。
> `
var callback = function(stream) {
  console.log('someone connected!');
};
server.on('connection', callback);
// ...
server.removeListener('connection', callback);
`

- 5	removeAllListeners([event])
移除所有事件的所有监听器， 如果指定事件，则移除指定事件的所有监听器。

- 6	setMaxListeners(n)
默认情况下， EventEmitters 如果你添加的监听器超过 10 个就会输出警告信息。 setMaxListeners 函数用于提高监听器的默认限制的数量。

- 7	listeners(event)
返回指定事件的监听器数组。

- 8	emit(event, [arg1], [arg2], [...])
按参数的顺序执行每个监听器，如果事件有注册监听返回 true，否则返回 false。
- 9 listenerCount(emitter, event)
返回指定事件的监听器数量。
####error事件
EventEmitter 定义了一个特殊的事件 error，它包含了错误的语义，我们在遇到 异常的时候通常会触发 error 事件。
当 error 被触发时，EventEmitter 规定如果没有响 应的监听器，Node.js 会把它当作异常，退出程序并输出错误信息。
我们一般要为会触发 error 事件的对象设置监听器，避免遇到错误后整个程序崩溃。例如：

```js
var events = require('events'); 
var emitter = new events.EventEmitter(); 
emitter.emit('error'); 
```


