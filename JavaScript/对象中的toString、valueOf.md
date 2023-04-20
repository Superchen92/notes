刷帖子看到个一道面试题，记录一下。

如何让下面条件成立
```js
if(a==1 && a==2 && a==3){
	console.log('win')
}

```

解决方案：
```js
const a = {
	value: 0,
	valueOf: function() {
		return ++this.value
	}
}

if(a == 1 && a == 2 && a == 3){
	console.log('win')
}
```

知识点：在JavaScript中 == 进行比较，如果其中一个是对象，一个是数字或字符串时，会尝试使用对象的valueOf()和toString()方法将对象转换为原始值。上述条件中，每一次执行 == 都会去调用一次valueOf() 函数。

ES6解法：
```js
const a = new Proxy({i: 0},{

    get: (target, name) => name === Symbol.toPrimitive ? () => ++target.i : target[name]

})
```


变式：
```js
if(a === 1 && a === 2 && a === 3){
	console.log('win')
}
```


解决方案：
```js
Object.defineProperties(window,{

    _a:{

        value: 0,

        writable: true

    },

    a: {

        get: function(){

            return ++_a

        }

    }

})
```

vue2的双向绑定实现原理就是基于Object.defineProperty

