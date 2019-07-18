<template>
  <div class="login_container">
    <div class="login_box">
      <!-- 图标log -->
      <div class="avatar_box">
        <img src="../assets/logo.png" alt="">
      </div>
      <el-form ref='loginFormRef' :model="loginForm" class="login_form" :rules='loginFormRules'>
        <!-- 登入框 -->
        <el-form-item prop='username'>
          <el-input prefix-icon="iconfont icon-user" v-model="loginForm.username"></el-input>
        </el-form-item>
        <!-- 密码框 -->
        <el-form-item prop='password'>
          <el-input type='password' prefix-icon="iconfont icon-3702mima" v-model="loginForm.password"></el-input>
        </el-form-item>
        <!-- 按钮框 -->
        <el-form-item class="btns">
          <el-button type="primary" round>登录</el-button>
          <el-button @click="resetLoginForm" type="success" round>重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>


<script>
export default {
  data(){
    return{
      loginForm:{
        username:'',
        password:''
      },
      loginFormRules:{
        username:[
          { required: true, message:'请输入用户名', trigger:'blur'},
          { min: 3, max: 10 , message:'长度在3到10个字符', trigger:'blur'}
        ],
        password:[
          { required: true, message:'请输入密码', trigger:'blur'},
          { min: 6, max: 15 , message:'长度在6到15个字符', trigger:'blur'}
        ]
      }
    }
  },
  methods:{
    resetLoginForm:function(){
      this.$refs.loginFormRef.resetFields()
    }
  }
}
</script>


<style lang='less' scoped>

.login_container{
  height: 100%;
  background-color: greenyellow;
}
.login_box{
  width: 450px;
  height: 300px;
  background-color: springgreen;
  box-shadow: 3px 0 15px black;
  border-radius: 5px;
  position:absolute;
  left: 50%;
  top:50%;
  transform: translate(-50%,-50%)
}
.avatar_box{
  height: 130px;
  width: 130px;
  border-radius: 50%;
  background: rgb(90, 221, 160);
  border: 1px solid rgb(0, 204, 255);
  overflow: hidden;
  box-shadow: 0 0 15px black;
  position: absolute;
  left: 50%;
  transform:translate(-50%,-50%);
  img{
    margin-top: 10px;
    width: 100%;
    height: 100%;
  }
}
.login_form{
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
.btns{
  display: flex;
  justify-content: flex-end;
}
@keyframes myavatar {
  100% {
    transform: rotate(100000deg);
  }
}
.avatar_box img:hover {
  animation: myavatar 20s ease;
}

</style>

