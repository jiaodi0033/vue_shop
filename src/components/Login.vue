<template>
  <div class="login-container">
    <div class="login-box">
<!--      头像区域-->
      <div class="avatar-box">
        <img src="../assets/logo.png">
      </div>
<!--      登录表单-->
      <el-form  class="login-form" label-width="0" ref="loginFormRef"
                :model="loginForm" :rules="loginFormRules">
        <el-form-item prop="username" >
          <el-input v-model="loginForm.username" prefix-icon="el-icon-s-custom"></el-input>
        </el-form-item>
        <el-form-item prop="password" >
          <el-input v-model="loginForm.password" type="password" prefix-icon="el-icon-lock" ></el-input>
        </el-form-item>
        <el-form-item class="login-btns">
          <el-button type="primary" @click="login">登录</el-button>
          <el-button type="info" @click="resetLoginForm">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      loginFormRules: {
        username: [
          { required: true, message: '用户名不能为空', trigger: 'blur' },
          { min: 6, max: 10, message: '长度在 6 到 10 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'blur' },
          { min: 6, max: 16, message: '长度在 6 到 16 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    resetLoginForm: function () {
      // console.log(this)
      this.$refs.loginFormRef.resetFields()
    },
    login () {
      console.log(this.loginForm)
      const isSuccess = true
      if (!isSuccess) return this.$message.error('登录失败')
      this.$message.success('登录成功')
      const token = 'thisisatoken'// 后台返回token数据
      window.sessionStorage.setItem('token', token)// 存储token到sessionStorage
      // 然后进行路由跳转
      this.$router.push('/home')
    }
  }
}
</script>

<style lang="less" scoped>
.login-container{
  background-color: #2b4b6b;
  height: 100%;
}
.login-box{
  width: 450px;
  height: 300px;
  background-color: #fff;
  position: absolute;
  left: 50%;
  top:50%;
  transform: translate(-50%,-50%);
}
.avatar-box{
  width: 100px;
  height: 100px;
  border: 1px solid #b6a3a3;
  border-radius: 50%;
  padding: 5px;
  box-shadow: 0 0 10px #ddd;
  position: absolute;
  left: 50%;
  transform: translate(-50%,-50%);
  background-color: #fff;
  img{
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background-color: #b6a3a3;
  }
}
.login-form{
  position: absolute;
  top:100px;
  width: 100%;
  padding: 0 25px;
  box-sizing: border-box;
}
.login-btns{
  float: right;
}
</style>
