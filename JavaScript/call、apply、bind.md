call、apply、bind 的作用是改变函数运行时this的指向

区别：
1. call传参时，第二个参数为参数列表
2. apply传参时，第二个参数为一个数组
3. bind传参时和call类似，但是bind不会直接执行，而是需要手动执行

```js
const name = '小明'
const age = 18
const db = {
	name: '小陈',
	age: 20,
}
const obj = {
	name: '小李',
	age: 25,
	objFn: function(param){
		console.log(`${this.name}的年龄是${this.age} ${param}`)
	} 
}

obj.objFn.call(db, param)
obj.objFn.apply(db, [param])
obj.objFn.apply(db, param)()
```
