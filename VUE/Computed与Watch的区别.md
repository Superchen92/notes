## Computed

计算属性，用于创建一个变量，它与创建一个方法相同，然后区别在于，计算属性的值会基于其响应式依赖被缓存。一个计算属性仅会在其响应式依赖更新时才重新计算。

计算属性默认是只读的，当你尝试修改它时，你会收到一个警告，你可以通过同时提供的getter和setter来创建。

```js
import { computed } from 'vue'

const demo = computed({
	get(){
		return something
	},
	set(newValue){
		something = newValue
	}
})
```

## Watch

计算属性允许我们声明性地计算衍生值。然而在有些情况下，我们需要在状态变化时执行一些“副作用”: 例如更改dom，或是异步操作的结果去修改另一处的状态。

```js
import { watch, ref } from 'vue'

const someOne = ref('')
watch(someOne, (newValue, oldValue) => {
	//to do something
})
```

监听的对象可以是一个ref对象(包括计算属性)、一个响应式对象、一个getter函数、或多个数据源组成的数组。

### 深层侦听器

直接传入一个响应式对象，会隐世地创建一个深层侦听器---该回调函数在所有嵌套的变更时都会被触发

```js
import { watch, reactive } from 'vue'
const soneOne = reactive({count: 0})

watch(obj, (newValue, oldVlaue) => {
	// 在嵌套的属性变更时触发 
	// 注意：`newValue` 此处和 `oldValue` 是相等的 
	// 因为它们是同一个对象！
})

someOne.count++
```


注意：不能直接监听响应式对象的属性值，只能监听一个响应式变量，如果要监听一个属性值，可以返回改属性的getter函数

## 区别

- computed支持缓存，watch不支持
- watch支持异步