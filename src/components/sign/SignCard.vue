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
      <el-form-item :label="formLabelAlign.userNameTitle" prop="userName">
        <el-input v-model="formLabelAlign.userName"></el-input>
      </el-form-item>
      <el-form-item :label="formLabelAlign.passWordTitle" prop="passWord">
        <el-input v-model="formLabelAlign.passWord"></el-input>
      </el-form-item>
    </el-form>
    <el-button
      style="width: 350px"
      round
      type="primary"
      @click="submitForm('formLabelAlign')"
    >
      {{ signSubmit }}
    </el-button>
    <div class="sign-page_card__footer">
      <el-link type="primary" v-for="(item, i) in signWay" v-bind:key="i">
        {{ item }}
      </el-link>
    </div>
  </el-card>
</template>

<script>
export default {
  data() {
    return {
      signTitle: "Welcome to RenderMe",
      signType: "Sign up",
      signSubmit: "Now Sign In",
      formLabelAlign: {
        userName: "",
        userNameTitle: "Username or email address",
        passWord: "",
        passWordTitle: "Password",
      },
      rules: {
        userName: [{ required: true, message: "请输入账号", trigger: "blur" }],
        passWord: [{ required: true, message: "请输入密码", trigger: "blur" }],
      },
      signWay: ["支付宝", "微信", "QQ", "微博"],
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
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
  color: #666769;
}
.sign-page_card__header {
  width: 100%;
  display: flex;
  justify-content: space-between;
}
.sign-page_card__footer {
  padding: 20px 0 0 0;
  margin-left: 20%;
  width: 60%;
  display: flex;
  justify-content: space-between;
}
</style>
