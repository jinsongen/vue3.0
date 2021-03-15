<template>
	<button @click="addCount">点击</button>
	<p>
		{{state}}
	</p>
</template>

<script>
	// import HelloWorld from './components/HelloWorld.vue'
	// console.log(obb)
	// setTimeout(()=>{
	// 	obb.a=222
	// },100)
	import {
		//ref监听 简单类型 变化
		ref,
		// reactive  监听复杂类型的变化
		reactive,
		shallowRef,
		triggerRef,
		toRaw,
		toRef,
		customRef
	} from "vue";

	function myRef(value) {
		return customRef((track, trigger) => {
			// track 追踪、
			return {
				set(setValue) {
					value = setValue
					trigger() // 触发视图变化
				},
				get() {
					track() //表示需要追踪变化
					return value
				}
			}
		})
	}
	let industry_list = [{
			"parent_ind": "女装",
			"name": "连衣裙"
		},{
			"parent_ind": "女装",
			"name": "连衣裙1"
		},{
			"parent_ind": "女装",
			"name": "女装2"
		},{
			"parent_ind": "女装",
			"name": "连衣裙3"
		},{
			"parent_ind": "女装",
			"name": "女装2"
		},
		{
			"parent_ind": "女装1",
			"name": "连衣裙1"
		},{
			"parent_ind": "女装1",
			"name": "连衣裙2"
		},{
			"parent_ind": "女装2",
			"name": "连衣裙3"
		},{
			"parent_ind": "女装2",
			"name": "连衣裙4"
		},{
			"parent_ind": "女装1",
			"name": "连衣裙21"
		},{
			"parent_ind": "女装1",
			"name": "连衣裙23"
		},{
			"parent_ind": "女装2",
			"name": "连衣裙33"
		},{
			"parent_ind": "女装2",
			"name": "连衣裙43"
		},
		{
			"name": "女装"
		},
		{
			"parent_ind": "女装",
			"name": "半身裙"
		},
		{
			"parent_ind": "女装",
			"name": "A字裙"
		},
		{
			"name": "数码"
		},
		{
			"parent_ind": "数码",
			"name": "电脑配件"
		},
		{
			"parent_ind": "电脑配件",
			"name": "内存"
		},
		{
			"parent_ind": "电脑配件",
			"name": "内存"
		},
	]
	export default {
		name: 'App',
		// 组合 api入口函数
		setup() {
			let obb = {
				a: 1
			};
			// let state = toRef(obb,"a")
			let state = myRef(obb.a)
			// let stateObj = toRaw(state)
			function addCount() {
				state.value += 1;
				console.log(obb, state)
			}
			return {
				state,
				addCount
			};
		},
		methods: {
			convert_format() {
				let newData = {};
				let list = JSON.parse(JSON.stringify(industry_list))
				industry_list.forEach((item, index, arr) => {
					if (!item.hasOwnProperty("parent_ind") && !newData.hasOwnProperty(item.name)) {
						newData[item.name] = convert_format(list, item.name)
						console.log(newData)
					}
				})

				function convert_format(list, parent_ind) {
					if (list.length) {
						let itemData = {}
						let newList = list;
						let second = [];
						newList = newList.filter(item=>{
							return item.hasOwnProperty("parent_ind")
						})
						newList.forEach((item,index,arr) => {
							if (item.parent_ind == parent_ind && !itemData.hasOwnProperty(item.name)) {
								delete newList[index].parent_ind
								itemData[item.name] = convert_format(newList, item.name);
							}
						})
						return itemData
					}
				}
			},
			convert_format2(){
				
					
					let newData = {};
					let list = JSON.parse(JSON.stringify(industry_list))
					industry_list.forEach((item, index, arr) => {
						if (!item.hasOwnProperty("parent_ind") && !newData.hasOwnProperty(item.name)) {
							newData[item.name] = convert_format(list, item.name)
							console.log(newData)
						}
					})
				
					function convert_format(list, parent_ind) {
						if (list.length) {
							let itemData = {}
							let newList = list;
							let second = [];
							// newList = newList.filter(item=>{
							// 	return item.hasOwnProperty("parent_ind")
							// })
							newList.forEach((item,index,arr) => {
								if (item.parent_ind == parent_ind && !itemData.hasOwnProperty(item.name)) {
									// delete newList[index].parent_ind
									itemData[item.name] = convert_format(newList, item.name);
								}
							})
							return itemData
						}
					}
				
			}
		},
		created() {
			var beginTime = +new Date();
			this.convert_format()
			var endTime = +new Date();
			console.log(endTime-beginTime)
			var beginTime = +new Date();
			this.convert_format2()
			var endTime = +new Date();
			console.log(endTime-beginTime)
		}
	}
</script>
