<template>
    <div class="login-wrap">
        <el-form :label-position="labelPosition" label-width="80px" :model="fromData">
            <h2>用户登录</h2>
            <el-form-item label="用户名">
                <el-input v-model="fromData.username"></el-input>
            </el-form-item>
            <el-form-item label="密码">
                <el-input v-model="fromData.password"></el-input>
            </el-form-item>
            <el-button type="primary">登录</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
  data() {
    return {
      fromData: {
        username: "",
        password: ""
      }
    };
  }
};
</script>

<style>
</style>
