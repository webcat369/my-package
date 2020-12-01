<template>
  <div class="home">
    <div class="title" @click="showPopUps">hello MessageBox</div>
    <MessageBox ref="messageBox" class="message-box" @closeMessage="close" :Width="500" :Height="250">
      <div class="my-message-box-header">
        <span>提示:</span>
      </div>
      <div class="my-message-box-content">
        <div class="my-message-box-message">
          <p>邮箱:</p>
        </div>
        <div class="my-message-box-input">
          <div class="my-input">
            <input type="text" placeholder="请输入邮箱" v-model="text" class="my-input-inner" ref='inputInner'>
          </div>
          <div class="my-message-box-errormsg" ref='err'>
            邮箱格式不正确
          </div>
        </div>
      </div>
      <div class="my-message-box-btns">
        <button type="button" @click="cancel">取消</button>
        <button type="button" @click="confirm">确认</button>
      </div>
    </MessageBox>
  </div>
</template>

<script>
import MessageBox from '@/components/MessageBox/MessageBox'
export default {
  name: 'home',
  components: {
    MessageBox
  },
  data () {
    return {
      text: ''
    }
  },
  methods: {
    // 显示弹框
    showPopUps () {
      this.$refs.messageBox.showMessage = true
    },
    // 取消按钮置空
    cancel () {
      this.text = ''
      this.$refs.err.style.visibility = 'hidden'
      this.$refs.inputInner.classList.remove('invalid')
    },
    // 关闭弹框
    close () {
      console.log('取消')
      this.text = ''
      this.$refs.err.style.visibility = 'hidden'
      this.$refs.inputInner.classList.remove('invalid')
      this.$refs.messageBox.showMessage = false
    },
    // 确认按钮提交
    confirm () {
      const Email = /^[A-Za-z\d]+([-_.][A-Za-z\d]+)*@([A-Za-z\d]+[-.])+[A-Za-z\d]{2,4}$/
      // 正则表达式的test方法：检测一个字符串是否匹配某个模式
      if (!Email.test(this.text)) {
        this.$refs.err.style.visibility = 'visible'
        this.$refs.inputInner.classList.add('invalid')
      } else {
        alert('你的邮箱是:' + this.text)
      }
    }
  }
}
</script>
<style scoped lang="scss">
.home{
  .title{
    color: #333;
  }
  .message-box{
    color: #333;
    .my-message-box-header{
      width: 100%;
      height: 60px;
      padding: 15px 15px;
      box-sizing: border-box;
      // background: peachpuff;
      line-height: 30px;
      span{
        font-size: 20px;
      }
    }
    .my-message-box-content{
      width: 100%;
      padding: 10px 15px;
      box-sizing: border-box;
      // background: pink;
      .my-message-box-message{
        width: 50px;
        p{
          font-size: 16px;
        }
      }
      .my-message-box-input{
        width: 100%;
        height: 60px;
        .my-input{
          width: 100%;
          height: 40px;
          border-radius: 5px;
          .my-input-inner{
            outline:none;
            width: 100%;
            height: 100%;
            padding: 0 15px;
            border-radius:6px;
            border:1px solid rgb(64,138,236);
            box-sizing: border-box;
            color: #606266;
            &.invalid{
              border:1px solid #f56c6c;
            }
          }
        }
        .my-message-box-errormsg{
          visibility: hidden;
          font-size: 14px;
          color: #f56c6c;
          margin-top: 2px;
        }
      }
    }
    .my-message-box-btns{
        width: 100%;
        height: auto;
        padding: 5px 15px 0;
        text-align: right;
        box-sizing: border-box;
        // background: plum;
        button{
          width:60px;
          height: 35px;
          border: 1px solid #dcdfe6;
          background:rgb(64,138,236);
          color: #ffffff;
          border-radius: 3px;
          margin-right: 15px;
          outline:none;
        }
        button:nth-of-type(1){
           background: oldlace;
           color: #606266;
        }
        button:nth-of-type(2){
           margin-right: 0;
           border-color:rgb(64,138,236);;
        }
    }
  }
}
</style>
