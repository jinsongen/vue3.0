<template>
	<button @click="addCount">点击</button>
	<p>
		{{state}}
	</p>
	<div ref="boxs"></div>
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
		customRef,
		onMounted,
		readonly,
		shallowReadonly
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
			let boxs = ref(null)
			let readonlyData = shallowReadonly({
				a:1,b:{
					b:1
				}
			})
			let readonlyData1 = readonly({
				a:1,b:{
					b:1
				}
			})
			readonlyData.a=2;
			readonlyData.b.b=2;
			readonlyData1.a=2;
			readonlyData1.b.b=2;
			console.log(readonlyData)
			console.log(readonlyData1)
			return {
				state,
				addCount,
				boxs
			};
		},
		methods: {},
		created() {}
	}
</script>
