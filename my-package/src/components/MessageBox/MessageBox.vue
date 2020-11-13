<template>
    <div class="box">
      <div class="mask"></div>
      <div class="content"></div>
    </div>
</template>

<script>
export default {
  name: 'MessageBox'
}
</script>

<style scoped lang="scss">
.box{
  z-index: 999;
  .mask{
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0,0,0,0.3);
  }
  .content{
    width: 500px;
    height: 350px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    background: #fff;
  }
}
</style>
