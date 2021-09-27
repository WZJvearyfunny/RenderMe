<template>
  <el-container class="sign-page_sty">
    <el-header class="sign-page_header">
      <img
        src="https://iconfont.alicdn.com/t/7862a342-1387-4589-9a23-5ec8bccbe68d.png"
        width="60px"
        style="border-radius: 30px"
      />
      <el-menu
        class="sign-page_header_menu"
        mode="horizontal"
        @select="handleSelect"
      >
        <el-submenu index="1">
          <template slot="title">Why RenderMe?</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title">我的工作台</template>
          <el-menu-item index="2-1">选项1</el-menu-item>
          <el-menu-item index="2-2">选项2</el-menu-item>
          <el-menu-item index="2-3">选项3</el-menu-item>
          <el-submenu index="2-4">
            <template slot="title">选项4</template>
            <el-menu-item index="2-4-1">选项1</el-menu-item>
            <el-menu-item index="2-4-2">选项2</el-menu-item>
            <el-menu-item index="2-4-3">选项3</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-menu-item index="3" disabled>消息中心</el-menu-item>
        <div class="sign-page_menu_button">
          <el-button size="small" @click="routeJump('0')">Sign Up</el-button>
          <el-button size="small" type="primary" @click="routeJump('1')"
            >Sign In</el-button
          >
        </div>
      </el-menu>
    </el-header>
    <el-main>
      <HomeCard
        imgsrcset="https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.webp"
        imgsrc="https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.jpg"
        hdec="Build like the best with RenderMe Enterprise"
        pdec="Take collaboration to the next level with security and administrative features built for teams."
        :buttonList="buttonList"
        @routeJump="routeJump"
      />
    </el-main>
    <el-footer>I'm studying now,xx!</el-footer>
  </el-container>
</template>

<script>
import HomeCard from "@/components/home/HomeCard.vue";
export default {
  name: "Home",
  components: {
    HomeCard,
  },
  data() {
    return {
      buttonList: [
        {
          title: "Start a free trial",
          titleFn: "routeJump",
          contact: "Contact Sales",
        },
      ],
    };
  },
  methods: {
    handleSelect(index, indexPath) {
      console.log("index", index);
      console.log("indexPath", indexPath);
    },
    routeJump(signtype) {
      console.log(signtype);
      this.$router.push({ path: "sign", query: { signtype } });
    },
  },
};
</script>
<style scoped>
.sign-page_sty {
  width: 100vw;
  height: 100vh;
}
.sign-page_header {
  display: flex;
  justify-content: center;
}
.sign-page_header_menu {
  width: 80%;
}
.sign-page_menu_button {
  position: absolute;
  right: 0;
  display: flex;
  align-items: center;
  height: 100%;
}
</style>
