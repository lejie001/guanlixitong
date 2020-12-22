<template>
<div class="qf-layout">

  <el-container>

    <el-aside width="150px">
      <QfAside></QfAside>
    </el-aside>

    <el-container class="qf-container">
      <div class="qf-container-wrap">
        <el-header height='60px'>
          <QfHeader></QfHeader>
        </el-header>
        <el-main>
          <QfMain></QfMain>
        </el-main>
      </div>
    </el-container>
  </el-container>
</div>
</template>

<script>
export default {
  components: {
    QfAside: ()=>import('./QfAside.vue'),
    QfHeader: ()=>import('./QfHeader.vue'),
    QfMain: ()=>import('./QfMain.vue')
  }
}
</script>

<style lang="scss" scoped>
.qf-aside {
  background-color: #545c64;
  height: 100%;
  color: #ddd;
  overflow: hidden;
}
.qf-header {
  background-color: white;
  line-height: 60px;
  padding-left: 20px;
  width: 100%;
}
.qf-main {
  background-color: white;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  padding: 20px;
  overflow: auto;
  min-width: 900px;
}
.el-container {
  height: 100%;
}
.qf-layout {
  height: 100%;
}
.el-aside {
  height: 100%;
  padding: 0;
}
.el-header {
  padding: 0;
}

</style>
