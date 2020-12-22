<template>
<div class="qf-app">
    <QfLayout></QfLayout>
</div>
</template>

<script>
// import routes from './pages/'
import { QfLayout } from '@/components/'

export default {
  name: 'App2',
  components: {
    QfLayout
  },
  data: function() {
    return {
      foo: 'hello foo'
    }
  },
  // 监听路由的变化
  watch: {
    // $route: function(to, from) {
    //   console.log('url发生了变化', to, from)
    // }
  }
}
</script>

<style>
html, body {
  padding: 0;
  margin: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.qf-app {
  height: 100%;
}
</style>
