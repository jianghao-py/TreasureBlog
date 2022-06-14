### Proxy

<br>

<br>

```javascript
	        //源数据
			let person = {
				name:'张三',
				age:18
			}

            const p = new Proxy(person,{
				//有人读取p的某个属性时调用
				get(target,propName){
					console.log(`有人读取了p身上的${propName}属性`)
					return Reflect.get(target,propName)
				},
				//有人修改p的某个属性、或给p追加某个属性时调用
				set(target,propName,value){
					console.log(`有人修改了p身上的${propName}属性，我要去更新界面了！`)
					Reflect.set(target,propName,value)
				},
				//有人删除p的某个属性时调用
				deleteProperty(target,propName){
					console.log(`有人删除了p身上的${propName}属性，我要去更新界面了！`)
					return Reflect.deleteProperty(target,propName)
				}
			})
```