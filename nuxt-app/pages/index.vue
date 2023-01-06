<template>
  <div>
    <NuxtLink to="/about">
      关于我们
    </NuxtLink>
    <NuxtLink to="/lend">
      我要投资
    </NuxtLink>
    <NuxtLink to="/user">
      用户中心
    </NuxtLink>
    <a href="http://atguigu.com" target="_blank">尚硅谷</a>

    <h1>Home page</h1>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    console.log('asyncData')
    let response = await $axios.$get('/')
    return {
      ip1: response, //这种写法的问题是：前面的远程调用是异步的，无法在这获取到response
    }
  },
  data() {
    return {
      ip: null,
    }
  },
  // created() {
  //   this.$axios.$get('http://icanhazip.com').then((response) => {
  //     console.log(response)
  //     this.ip = response
  //   })
  // },
}
</script>
