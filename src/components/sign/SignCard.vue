<template>
  <el-card class="sign-page_card">
    <div slot="header">
      <div class="sign-page_card__header">
        <el-link icon="el-icon-back" :underline="false" href='/'>Home</el-link>
        <div class="sign-page_card__header_signTitle">
          <label>{{ signTitle }}</label>
        </div>
        <el-link style="width: 70px" type="primary" @click="changeSign">
          {{ signStatus }}
        </el-link>
      </div>
    </div>
    <el-form
      style="text-align: left"
      label-position="top"
      label-width="80px"
      :model="formLabelAlign"
      ref="formLabelAlign"
      :rules="rules"
      v-show="signType === '1'"
      size="mini"
    >
      <el-form-item :label="formLabelAlign.userNameTitle" prop="userName">
        <el-input v-model="formLabelAlign.userName"></el-input>
      </el-form-item>
      <el-form-item :label="formLabelAlign.passWordTitle" prop="passWord">
        <el-input
          v-model="formLabelAlign.passWord"
          autocomplete="off"
        ></el-input>
      </el-form-item>
    </el-form>
    <el-form
      style="text-align: left"
      label-position="top"
      label-width="80px"
      :model="formLabelAlignUp"
      ref="formLabelAlignUp"
      :rules="rulesUp"
      v-show="signType === '0'"
      size="mini"
    >
      <el-form-item :label="formLabelAlignUp.userNameTitle" prop="userName">
        <el-input v-model="formLabelAlignUp.userName"></el-input>
      </el-form-item>
      <el-form-item :label="formLabelAlignUp.passWordTitle" prop="passWord">
        <el-input
          v-model="formLabelAlignUp.passWord"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item
        :label="formLabelAlignUp.passWordCheckTitle"
        prop="passWordCheck"
      >
        <el-input
          v-model="formLabelAlignUp.passWordCheck"
          autocomplete="off"
        ></el-input>
      </el-form-item>
    </el-form>
    <el-button style="width: 350px" round type="primary" @click="submitForm()">
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
  props: ["signType"],
  data() {
    var validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请再次输入密码"));
      } else if (value !== this.formLabelAlignUp.passWord) {
        callback(new Error("两次密码不一致"));
      } else {
        callback();
      }
    };
    return {
      signTitle: "",
      signStatus: "",
      signSubmit: "Now Sign In",
      formLabelAlign: {
        userName: "",
        userNameTitle: "Username or email address",
        passWord: "",
        passWordTitle: "Password",
      },
      formLabelAlignUp: {
        userName: "",
        userNameTitle: "Enter your or email address",
        passWord: "",
        passWordTitle: "Enter your password",
        passWordCheck: "",
        passWordCheckTitle: "Check your password",
      },
      rules: {
        userName: [{ required: true, message: "请输入账号", trigger: "blur" }],
        passWord: [{ required: true, message: "请输入密码", trigger: "blur" }],
      },
      rulesUp: {
        userName: [{ required: true, message: "请输入账号", trigger: "blur" }],
        passWord: [{ required: true, message: "请输入密码", trigger: "blur" }],
        passWordCheck: [
          {
            required: true,
            validator: validatePass,
            trigger: "blur",
          },
        ],
      },
      signWay: ["支付宝", "微信", "QQ", "微博"],
    };
  },
  created() {
    this.signType === "0"
      ? ((this.signStatus = "Sign in"),
        (this.signSubmit = "Now Sign Up"),
        (this.signTitle = "Sign up to RenderMe"))
      : ((this.signStatus = "Sign up"),
        (this.signSubmit = "Now Sign In"),
        (this.signTitle = "Sign in to RenderMe"));
  },
  methods: {
    submitForm() {
      let formName =
        this.signType === "0" ? "formLabelAlignUp" : "formLabelAlign";
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    changeSign() {
      this.$emit("changeSign");
      this.signType === "0"
        ? ((this.signStatus = "Sign up"),
          (this.signSubmit = "Now Sign In"),
          (this.signTitle = "Sign in to RenderMe"))
        : ((this.signStatus = "Sign in"),
          (this.signSubmit = "Now Sign Up"),
          (this.signTitle = "Sign up to RenderMe"));
    },
  },
};
</script>

<style scoped>
.sign-page_card {
  width: 400px;
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
