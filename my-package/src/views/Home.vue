<template>
  <div class="home">
    <MessageBox></MessageBox>
    <div class="title">hello world</div>
  </div>
</template>

<script>
import MessageBox from '@/components/MessageBox/MessageBox'
export default {
  name: 'Home',
  components: {
    MessageBox
  }
}
</script>
<style scoped lang="scss">
.home{
  .title{
    width: 100%;
    height: 100px;
    background: peachpuff;
  }
}
</style>
