###Vue 起步
####引入cdn

```js
<script src="https://unpkg.com/vue/dist/vue.js"></script>
```
你看到的 v-bind 属性被称为指令。指令带有前缀 v-，以表示它们是 Vue 提供的特殊属性。可能你已经猜到了，它们会在渲染的 DOM 上应用特殊的响应式行为。简言之，这里该指令的作用是：“将这个元素节点的 title 属性和 Vue 实例的 message 属性保持一致”。

```js
<div id="app-2">
  		<span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
  		</span>
</div>
js:
	var app2 = new Vue({
  
  		el: '#app-2',
  		
  		data: {
    
    		message: '页面加载于 ' + new Date()
  }
})

```
####条件与循环

```html
html:
<div id="app-3">
  		<p v-if="seen">现在你看到我了</p>
	</div>
	<div id="app-4">
  		<ol>
    		<li v-for="todo in todos">
      			{{ todo.text }}
    		</li>
  		</ol>
	</div>
```
```js
js:
var app3 = new Vue({
  		el: '#app-3',
  		data: {
   		seen: true
  }
})
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: '学习 JavaScript' },
      { text: '学习 Vue' },
      { text: '整个牛项目' }
    ]
  }
})
```
####用户交互
用 v-on 指令绑定一个调用 Vue 实例方法的事件监听器：

```html
<div id="app-5">
  		<p>{{ message }}</p>
  		<button v-on:click="reverseMessage">逆转消息</button>
</div>
```
```js
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
Vue 还提供了 v-model 指令，使表单输入和应用状态间的双向绑定变得轻而易举。

```html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
```js
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```

