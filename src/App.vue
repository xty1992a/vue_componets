<template>
  <div id="app">
    <div class="wrap" ref="wrap">
      <div class="inner">
      </div>
    </div>
    <router-view></router-view>

  </div>
</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: 'app',
    created () {
      this.$nextTick(() => {
        this.scroll = new BScroll(this.$refs.wrap, {
          scrollX: true,
          click: true
        })
      })
    }
  }
</script>

<style rel="stylesheet/less" lang="less">
  @rem: 75rem;
  *{
    padding: 0;
    margin: 0;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    .wrap {
      background-color: #f7e800;
      width: 750/@rem;
      height: 400/@rem;
      margin: 0 auto;
      overflow: hidden;
      .inner {
        width: 1200px;
        height: 100%;
        background: repeating-linear-gradient(to left, #fff 0px, #fff 10px, #000 10px, #000 20px);
      }
    }
  }
</style>
