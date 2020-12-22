<template>
<div>
  <h1>首页</h1>
</div>
</template>

<script>
export default {
  mounted() {
    console.log('$route', this.$route)
    console.log('$router', this.$router)
  },
  methods: {
    skipToUser() {
      // 【编程式路由跳转的三种写法】
      // 1、使用path来跳转
      // this.$router.push('/useroiwioewoieoioiewoiewoiewoiewi')
      // 2、使用路由别名
      // this.$router.push('/u')
      // 3、命名路由命名
      this.$router.push({name:'me'})
    }
  }
}
</script>

<style lang="css" scoped>

</style>
