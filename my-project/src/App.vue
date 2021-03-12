<template>
	<button @click="addCount">点击</button>
<p>
	{{count}}
</p>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import {
	//ref监听 简单类型 变化
	ref,
	// reactive  监听复杂类型的变化
	reactive
	} from "vue";
export default {
  name: 'App',
  // 组合 api入口函数
  setup(){
	  // let count = 0; //无法监听
	  //  利用ref  定义一个count 变量 初始值是0
	  // 可以触发 监听更新
	  // 利用ref 定义的变量 ==》对象 包含 
	  /* __v_isRef: true
	  _rawValue: 1
	  _shallow: false
	  _value: 1
	  value: (...) */
	  let count = ref(0);
	  // 组合api 的变量 return返回
	  let addCount = function(){
		  console.log(count.value)
		  count.value+=1
	  }
	  
	  let 
	  return {
		  count,addCount
	  }
  },
  methods:{}
}
</script>
