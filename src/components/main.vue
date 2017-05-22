<template>
  <div class="hello">
    <child>
      <h2 slot="head">我希望能出现在child内部</h2>
      <h2 slot="body">body</h2>
    </child>
    <sbling>
      <h2>我来自父组件</h2>
    </sbling>
    <button @click="isShow=true">警告</button>
    <img-viewer></img-viewer>
    <transition name="modal">
      <modal v-show="isShow" @hide="isShow = !isShow" @time="selecteTime">
        <timer></timer>
      </modal>
    </transition>
  </div>
</template>

<script>
  import child from './child.vue'
  import sbling from './sbling.vue'
  import modal from './modal.vue'
  import timer from './timer.vue'
  import imgViewer from './img_viewer.vue'
  export default {
    name: 'main',
    data () {
      return {
        isShow: true
      }
    },
    methods: {
      selecteTime (time) {
        console.log(time)
      }
    },
    components: {
      child,
      sbling,
      modal,
      timer,
      imgViewer
    },
    created () {
      console.log(this.$store)
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style rel="stylesheet/less" lang="less">
  .mask, .bottom{
  }
  .modal-enter, .modal-leave-active{
    &.mask{
      opacity: 0;
      .bottom{
        transform: translateY(100%);
      }
    }
  }
  .modal-enter-active, .modal-leave-active{
    transition: .5s;
    &.mask{
      .bottom{
        transition: .5s;
      }
    }
  }
  .modal-leave{
    transition: 2s;
    &.mask{
      opacity: 1;
      .bottom{
        transform: translateY(0);
      }
    }
  }
</style>
