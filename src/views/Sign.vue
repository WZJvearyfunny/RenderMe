<template>
  <el-container class="sign-page_sty">
    <!-- <el-header ref="header">Header</el-header> -->
    <el-main id="sign-page_main">
      <el-avatar :size="120" :src="avatar"></el-avatar>
      <div class="sign-page_title">
        <label>
          <h1>{{ userName }}</h1>
          <h2 style="color: #666">{{ signTitle }}</h2>
        </label>
      </div>
      <SignCard @changeSign="changeSign" :signType="signType" />
    </el-main>
    <el-footer>I'm studying now,xx!</el-footer>
  </el-container>
</template>

<script>
import SignCard from "@/components/sign/SignCard.vue";
export default {
  components: {
    SignCard,
  },
  data() {
    return {
      signType: "1", //0 注册，1 登录
      signTitle: "Welcome to RenderMe",
      avatar: "",
      initAvatar: [
        "https://iconfont.alicdn.com/t/2fe81ecd-b859-464c-aeca-3fa28c9c9aff.png",
        "https://iconfont.alicdn.com/t/fb3d1a3f-0347-44e6-ac19-0abe90286682.png",
        "https://iconfont.alicdn.com/t/7ccce21b-d9a7-4832-b8e2-a8ae3b340ba4.png",
        "https://iconfont.alicdn.com/t/11004990-10df-451e-bfb4-38cdc695e6a5.png",
        "https://iconfont.alicdn.com/t/49b7f67c-309f-46b2-ba48-de0e7842a756.png",
        "https://iconfont.alicdn.com/t/fd7da8ea-9ee7-4433-b1cf-43bb5932bb96.png",
        "https://iconfont.alicdn.com/t/a5771840-9a03-41c9-902f-95033c76ec61.png",
        "https://iconfont.alicdn.com/t/fd7da8ea-9ee7-4433-b1cf-43bb5932bb96.png",
        "https://iconfont.alicdn.com/t/59875555-057b-46f4-8897-f732a394ea45.png",
        "https://iconfont.alicdn.com/t/c62b1eb7-29ab-4992-bf3e-ccbdfcd8a13b.png",
      ],
      userName: "",
    };
  },
  created() {
    this.signType = this.$route.query.signtype || "0";
    this.ranDomAvatar();
    this.signType === "0"
      ? (this.userName = "User Name")
      : (this.userName = "WZJ");
  },
  methods: {
    ranDomAvatar() {
      this.avatar = this.initAvatar[~~(Math.random() * 10)];
    },
    changeSign() {
      this.signType === "0"
        ? ((this.signType = "1"), (this.userName = "WZJ"))
        : ((this.signType = "0"), (this.userName = "User Name"));
    },
  },
};
</script>

<style>
#sign-page_main {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.sign-page_sty {
  width: 100vw;
  height: 100vh;
}
.sign-page_title {
  margin-bottom: 15px;
  color: #3a7ac4;
  text-align: center;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
</style>
