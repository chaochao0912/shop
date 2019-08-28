<template>
  <div class="login">
  <el-form  :model="form" label-width="80px" :rules="rules" status-icon ref="form">
    <img src="../assets/timg.jpg" alt="">
  <el-form-item label="用户名" prop='username'>
    <el-input v-model="form.username" placeholder="请输入用户名"></el-input>
  </el-form-item>
    <el-form-item label="密码" prop="password">
    <el-input  type="password" v-model="form.password" placeholder="请输入密码"></el-input>
  </el-form-item>
  <el-form-item >
   <el-button type="primary" class="loginbtn" @click="loginb">登录</el-button>
   <el-button @click="reset">重置</el-button>
  </el-form-item>
</el-form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      form: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 5, message: '长度请在3至5个字符间', trigger: ['change', 'blur'] }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 12, message: '长度请在6至12个字符间', trigger: ['change', 'blur'] }
        ]
      }
    }
  },
  methods: {
    reset () {
      this.$refs.form.resetFields()
    },
    loginb () {
      // console.log(111)
      this.$refs.form.validate(valid => {
        if (!valid) return
        console.log(222)

        axios.post('http://localhost:8888/api/private/v1/login', this.form).then(res => {
          console.log(res)
          const { meta, data } = res.data
          if (meta.status === 200) {
            console.log(meta.msg)

            localStorage.setItem('token', data.token)
            this.$message({
              message: meta.msg,
              type: 'success',
              duration: 1000
            })

            this.$router.push('/index')
          } else {
            this.$message.error(meta.msg)
          }
        })
      })
    }
  }
}
</script>

<style lang ="scss">
.login{
  width:100%;
  height: 100%;
  background-color: #2d434c;
  overflow: hidden;

 .el-form {
  width: 400px;
  padding:20px;
  padding-top: 70px;
  margin: 0 auto;
  background-color: #fff;
  margin-top:200px;
  position: relative;

  .loginbtn {
    margin-right: 60px;
  }
  img {
    width:120px;
    height: 120px;
    position: absolute;
    left:50%;
    transform: translate(-50%);
    border-radius: 50%;
    top:-75px;
    border:5px solid #fff;
  }
}
}

</style>
