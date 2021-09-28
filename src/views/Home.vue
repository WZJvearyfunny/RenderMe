<template>
  <el-container class="page_sty">
    <el-header class="page_header" v-if="false">
      <img
        src="https://iconfont.alicdn.com/t/7862a342-1387-4589-9a23-5ec8bccbe68d.png"
        width="60px"
        style="border-radius: 30px"
      />
      <el-menu
        class="page_header_menu"
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
        <div class="page_menu_button">
          <el-button size="small" @click="routeJump('0')">Sign Up</el-button>
          <el-button size="small" type="primary" @click="routeJump('1')"
            >Sign In</el-button
          >
        </div>
      </el-menu>
    </el-header>
    <el-main>
      <div class="homepage-main_top">
        <div style="width: 90%">
          <div class="homepage-main_top_space">
            <div class="homepage-main_top_space_center">
              <h1 class="homepage-main_top_space_center_title">
                Where the world builds software
              </h1>
              <p class="homepage-main_top_space_center_dec">
                Millions of developers and companies build, ship, and maintain
                their software on GitHub—the largest and most advanced
                development platform in the world.
              </p>
              <div class="homepage-main_top_space_center_sign">
                <el-input
                  placeholder="Email address"
                  v-model="emailAddress"
                  clearable
                >
                </el-input>
                <el-button type="success" size="medium">
                  Sign up for GitHub
                </el-button>
              </div>
            </div>
            <div></div>
          </div>
          <el-divider class="homepage-main_top_divider"></el-divider>
          <div class="homepage-main_top_tag">
            <div v-for="(item, index) in topTag" v-bind:key="index">
              <div class="homepage-main_top_tag__title">{{ item.title }}</div>
              <div class="homepage-main_top_tag__dec">{{ item.desc }}</div>
            </div>
          </div>
        </div>
      </div>
      <HomeCard
        imgsrcset="https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.webp"
        imgsrc="https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.jpg"
        hdec="Build like the best with RenderMe Enterprise"
        pdec="Take collaboration to the next level with security and administrative features built for teams."
        :buttonList="buttonList"
        @routeJump="routeJump"
        ref="homecard"
      />
      <div class="homepage-main_actmenu">
        <div class="homepage-main_actmenu__grid">
          <div>Code</div>
          <div>Collaborate</div>
          <div>Develop</div>
          <div>Automate</div>
          <div>Secure</div>
          <div>Community</div>
        </div>
      </div>
      <div style="width: 100%; height: 1080px">123</div>
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
      emailAddress: "",
      topTag: [
        {
          title: "65+ million",
          desc: "Developers",
        },
        {
          title: "3+ million",
          desc: "Organizations",
        },
        {
          title: "200+ million",
          desc: "Repositories",
        },
        {
          title: "72%",
          desc: "Fortune 50",
        },
      ],
    };
  },
  mounted() {
    const that = this;
    document
      .getElementsByClassName("el-main")[0]
      .addEventListener("scroll", function () {
        console.log("页面滚动事件");
        console.dir(that.$refs.homecard.$el);
      });
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
    getScroll() {
      console.log("112233");
    },
  },
};
</script>
<style scoped>
.page_sty {
  width: 100vw;
  height: 100vh;
}
.page_header {
  display: flex;
  justify-content: center;
}
.page_header_menu {
  width: 90%;
}
.page_menu_button {
  position: absolute;
  right: 0;
  display: flex;
  align-items: center;
  height: 100%;
}
.homepage-main_top {
  width: 100%;
  height: 690px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.homepage-main_top_space {
  display: grid;
  grid-template-columns: 1fr 1fr;
  height: 524px;
}
.homepage-main_top_tag {
  width: 80%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.homepage-main_top_tag__title {
  font-size: 20px !important;
  line-height: 28px !important;
  text-align: left;
}
.homepage-main_top_tag__dec {
  color: rgba(0, 0, 0, 0.7) !important;
  font-size: 12px !important;
  line-height: 20px !important;
  text-align: left;
}
.homepage-main_top_space_center {
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.homepage-main_top_space_center_title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 72px !important;
  line-height: 76px !important;
  text-align: left;
  color: #666;
}
.homepage-main_top_space_center_dec {
  font-size: 24px !important;
  line-height: 32px !important;
  text-align: left;
  color: #8193b2 !important;
}
.homepage-main_top_space_center_sign {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-column-gap: 20px;
  margin-right: 15%;
}
.homepage-main_actmenu {
  margin-top: 5%;
  width: 100%;
  display: flex;
  justify-content: center;
  position: sticky;
  top: 0px;
}
.homepage-main_actmenu__grid {
  width: 90%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
  color: #24292f;
  font-size: 16px !important;
  line-height: 24px !important;
}
>>> .el-button--success {
  color: #fff;
  background-color: #54a459;
  border-color: #54a459;
}
</style>
