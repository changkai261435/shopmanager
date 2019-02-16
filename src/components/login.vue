<template>
  <div class="login-wrap">
    <el-form label-position="top" label-width="80px" :model="fromData" class="login-form">
      <h2>用户登录</h2>
      <el-form-item label="用户名">
        <el-input v-model="fromData.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="fromData.password"></el-input>
      </el-form-item>
      <el-button @click.prevent='handlelogin()' type="primary" class="login-button">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      fromData: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async handlelogin () {
      const res = await this.$http.post(`login`, this.fromData)
      const { data: { data: { token }, meta: { msg, status } } } = res
      if (status === 200) {
        localStorage.setItem('token', token)
        // 渲染home。vue
        this.$router.push({
          name: 'home'
        })
      } else {
        // 用户名密码错误提示
        this.$message.error(msg)
      }
      // .then(res => {
      //   console.log(res);
      //   const { data: { data, meta: { msg, status } } } = res;
      //   if (status === 200) {
      //     //渲染home。vue
      //     this.$router.push({
      //       name:'home'
      //     })

      //   } else {
      //     //用户名密码错误提示
      //     this.$message.error(msg)
      //   }
      // // });
    }
  }
}
</script>

<style>
.login-wrap {
  background-color: #324152;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.login-wrap .login-form {
  background-color: #fff;
  width: 400px;
  padding: 30px;
  border-radius: 5px;
}
.login-wrap .login-form .login-button {
  width: 100%;
}
</style>
