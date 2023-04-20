```js

const data = [1,2,3,4,5,6,7,8,9]

const killPromise = (value) => {

	return new Promise((resolve, reject) => {
	
		setTimeout(() => {
	
			resolve(value)
	
		}, 2000)
	
	})

}



async function demo1() {

	for(let i = 0; i < 10; i++){

		const res = await killPromise(i)

		console.log(res)

	}

}



function demo2(){

	console.log('start')

	const res = data.map(async item => {

		return await killPromise(item)

	})

	const resPromise = await Promise.all(res)

	//console.log(res)

	//console.log('end')

}



demo1()
```

