<template>
  <div class="home">
    <div class="title" @click="showPopUps">hello MessageBox</div>
    <MessageBox ref="messageBox" class="messageBox" :Width="500" :Height="350">
      <div class="messageContent">
        <p>提示：</p>
        <p>检测到未保存的内容，是否在离开页面前保存修改？</p>
      </div>
      <div class="messageButton">
        <button type="button">取消</button>
        <button type="button">确认</button>
      </div>
    </MessageBox>
  </div>
</template>

<script>
import MessageBox from '@/components/MessageBox/MessageBox'
export default {
  name: 'Home',
  components: {
    MessageBox
  },
  methods: {
    showPopUps () {
      this.$refs.messageBox.showMessage = true
    }
  }
}
</script>
<style scoped lang="scss">
.home{
  .title{
  }
  .messageBox{
    .messageContent{
      p{
        color: #333;
      }
      p:nth-of-type(1){
        font-size: 28px;
      }
      p:nth-of-type(2){
        font-size: 18px;
        padding-left: 35px;
      }
    }
    .messageButton{
      position: absolute;
      bottom: 20px;
      right: 20px;
        button{
          width:60px;
          height: 35px;
          border: none;
          background: rgb(102,177,255);
          color: #ffffff;
          border-radius: 10px;
          margin-right: 15px;
          outline:none;
        }
    }
  }
}
</style>
