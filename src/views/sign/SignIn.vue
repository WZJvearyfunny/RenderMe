<template>
  <el-container class="sign-page_sty">
    <el-header>Header</el-header>
    <el-main id="sign-page_main">
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
  justify-content: center;
}
.sign-page_sty {
  width: 100vw;
  height: 100vh;
}
</style>
