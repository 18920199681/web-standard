# JavaScript 规范

* #### 关键字后面加空格。

不推荐

``` text
if(condition){
    ...
}
```

推荐

``` javascript
if (condition) {
    ...
}
```

* #### 始终使用 === 替代 ==。

例外： obj == null 可以用来检查 null || undefined。

* #### 字符串拼接操作符 (Infix operators) 之间要留空格。

不推荐

``` text
let name = 'adam';
let message = 'hello,'+name+'!';
```

推荐

``` javascript
let name = 'adam';
let message = 'hello,' + name + '!';
```

* #### 逗号后面加空格。

* #### else 关键字要与花括号保持在同一行。

* #### 不要丢掉异常处理中err参数。

不推荐

``` javascript
fnTest(function(err) {
	console.log('todo');
})
```

推荐

``` javascript
fnTest(function(err) {
	if (err) throw err;
	console.log('todo');
})
```

* #### 点号操作符与属性在同一行。

不推荐

``` javascript
console.
log('hello');
```

推荐

``` javascript
console
    .log('hello');
```

* #### 键值对之间正确留白

不推荐

``` text
let obj = { 'key' : 'value' }
let obj = { 'key' :'value' }
let obj = { 'key':'value' }
```

推荐

``` text
let obj = { 'key': 'value' }
```

* #### 尽量避免三元运算符


``` javascript
let num = val ? val : 0;
```

可以写成

``` javascript
let num = val || 0;
```

* #### 如果条件语句中有 return，避免使用 else

不推荐
``` javascript
if (test === 1) {
	todo;
	return 'a';
} else {
	todo;
	return 'b';
}
```

推荐

``` javascript
if (test === 1) {
	todo;
	return 'a';
}

todo;
return 'b';
```

* #### 无返回值也可巧用 return 简化条件语句

``` javascript
if (test === 1) {
	todo;
} else {
	todo;
}
```

可以写成

``` javascript
if (test === 1) {
	todo;
	return;
}

todo;
```

<font style="color: red">* 前提要保证return后面的逻辑通畅</font>

* #### 异步请求建议使用es7语法糖 async...await, 减少嵌套，使语句更清晰

不推荐

``` javascript
renderTest({ commit }, params) {
	return new Promise(resolve => {
		Vue.prototype.$http.post("RENDER_TEST", params).then(res => {
			commit("MU_RENDER_TEST", res.data);
			resolve();
		})
	})
}
```

推荐

``` javascript
async renderTest({ commit }) {
	const res = await Vue.prototype.$http.post("RENDER_TEST", params);

	if (res.code !== 0) return false;

	commit("MU_RENDER_TEST", res.data);

	return res;
}
```
