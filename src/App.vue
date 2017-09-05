<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
  * {
    padding: 0;
    margin: 0;
    border: none;
    box-sizing: border-box;
    outline: none;
    -webkit-overflow-scrolling: touch;
    tap-highlight-color: transparent;

    font-family: 'PingFangSC-Regular', Helvetica, Tahoma, Arial, STXihei, '华文细黑', 'Microsoft YaHei', '微软雅黑', SimSun, '宋体', Heiti, '黑体', sans-serif;
  }
  #app {

  }
</style>
