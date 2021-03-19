<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>
<script>
	import {defineComponent} from "vue";
	export default defineComponent({
		mounted(){
			# 阿拉钉
			1. css 布局 垂直水平居中
			2. BFC了解嘛 块格式化上下文 (Block Formatting Context)
			3. 类型判断
			4. 基础数据类型 和 引用数据类型 区别
			5. instanceof 底层实现
			6. new vue 干了什么
			7. data 里面声明拉一个[] 在 mounted 里面改变 length 长度 干了什么  页面数据会变化嘛、 如何改变
			8. vm.$set 干了什么 怎么使用
			9. 对象新增属性 底层干了什么
			10. vuex 的属性都有哪些
			11. modules 现有module a 和 mudule b  我想在a里面使用b的mutation 怎么做
			12. vuex 的优势有哪些
		}
	})
</script>
<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
