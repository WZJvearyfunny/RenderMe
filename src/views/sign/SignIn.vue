<template>
  <el-container class="sign-page_sty">
    <el-header>Header</el-header>
    <el-main id="sign-page_main">
      <el-avatar
        :size="100"
        src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
      ></el-avatar>
      <div class="sign-page_title"><h1>Sign in to RenderMe</h1></div>

      <SignCard />
    </el-main>
    <el-footer>Footer</el-footer>
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
      msg: "123",
    };
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
