<template>
  <el-card class="sign-page_card">
    <div slot="header">
      <div class="sign-page_card__header">
        <div></div>
        <div class="sign-page_card__header_signTitle">{{ signTitle }}</div>
        <el-link type="primary">{{ signType }}</el-link>
      </div>
    </div>
    <el-form
      style="text-align: left"
      label-position="top"
      label-width="80px"
      :model="formLabelAlign"
      ref="formLabelAlign"
      :rules="rules"
    >
      <el-form-item label="Username or email address" prop="userName">
        <el-input v-model="formLabelAlign.userName"></el-input>
      </el-form-item>
      <el-form-item label="Password" prop="passWord">
        <el-input v-model="formLabelAlign.passWord"></el-input>
      </el-form-item>
    </el-form>
    <el-button
      style="width: 350px"
      round
      type="primary"
      @click="submitForm('ruleForm')"
    >
      {{ signSubmit }}
    </el-button>
  </el-card>
</template>

<script>
export default {
  data() {
    return {
      signTitle: "登录",
      signType: "注册",
      signSubmit: "立即登录",
      formLabelAlign: {
        userName: "",
        passWord: "",
      },
      rules: {
        userName: [{ required: true, message: "请输入账号", trigger: "blur" }],
        passWord: [{ required: true, message: "请输入密码", trigger: "blur" }],
      },
    };
  },
};
</script>

<style scoped>
.sign-page_card {
  width: 400px;
  height: 450px;
}
.sign-page_card__header_signTitle {
  font-size: 20px;
  color: var(--color-fg-default);
}
.sign-page_card__header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  /* justify-content: end; */
}
</style>
