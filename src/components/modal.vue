<template>
  <div class="mask" @click="hide">
    我是模态框
    <div class="bottom" @click.stop>
      <slot></slot>
      <div class="btn_wrap">
        <button @click="ok">确定</button>
        <button @click="cancel">取消</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'modal',
    data () {
      return {}
    },
    methods: {
      hide () {
        console.log('hide')
        this.$emit('hide')
      },
      ok () {

      },
      test (index) {
        console.log(index, 'modal')
      },
      cancel () {
        console.log('test')
      }
    }
  }
</script>

<style rel="stylesheet/less" lang="less">
  .mask{
    background-color: rgba(0,0,0,.5);
    position: fixed;
    bottom: 0;
    right: 0;
    left: 0;
    top: 0;
    .bottom{
      position: absolute;
      width: 100%;
      bottom: 0;
    }
  }
</style>
