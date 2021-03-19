<template>
  <div>
    <ul>
      <li><nuxt-link :to="{name:'index'}">首页1</nuxt-link></li>
      <li><nuxt-link :to="{name:'about-id',params:{id:1}}">About</nuxt-link></li>
      <li><nuxt-link :to="{name:'news'}">News</nuxt-link></li>
    </ul>
  </div>
</template>
<script>

</script>
