<template>
  <div class="box" v-show="showMessage">
      <div class="mask"></div>
      <div class="content" :style="{width:`${Width}px`,height:`${Height}px`}">
        <slot></slot>
        <div class="close" @click="closePopUps">
          <img src="../../assets/images/close.svg" alt="">
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'MessageBox',
  data () {
    return {
      showMessage: false
    }
  },
  props: {
    Width: {
      type: Number,
      default: 500,
      required: false
    },
    Height: {
      type: Number,
      default: 350,
      required: false
    }
  },
  methods: {
    closePopUps () {
      this.showMessage = false
    }
  }
}
</script>

<style scoped lang="scss">
.box{
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  .mask{
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.3);
  }
  .content{
    //width: 500px;
    //height: 350px;
    position: relative;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    background: #fff;
    border-radius: 10px;
    box-sizing: border-box;
    .close{
      width:30px;
      height: 30px;
      position: absolute;
      right:-10%;
      top: -5%;
      transform: translate(-50%,-50%);
      img{
        width: 100%;
      }
    }
  }
}
</style>
