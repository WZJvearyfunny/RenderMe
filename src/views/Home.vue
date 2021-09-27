<template>
  <el-container class="sign-page_sty">
    <el-header>
      <el-menu class="el-menu-demo" mode="horizontal" @select="handleSelect">
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
        <el-menu-item
          index="4"
          style="
            width: 950px;
            display: flex;
            justify-content: end;
            align-items: center;
          "
        >
          <el-button size="small">注册</el-button>
          <el-button size="small" type="primary">登录</el-button>
        </el-menu-item>
      </el-menu>
    </el-header>
    <el-main>
      <div class="home-main_picture">
        <div class="home-main_picture1__connet">
          <div
            class="home-main_picture1__connet_title"
            style="max-width: 310px"
          >
            <label>
              <h2
                style="
                  font-size: 24px !important;
                  line-height: 28px !important;
                  font-weight: 800 !important;
                  margin-block-start: 0;
                  margin-block-end: 0;
                "
              >
                Build like the best with RenderMe Enterprise
              </h2>
            </label>
            <label>
              <p>
                Take collaboration to the next level with security and
                administrative features built for teams.
              </p>
            </label>
            <div>
              <el-button>Start a free trial</el-button>
              <el-link type="primary" style="margin-left: 15%">
                Contact Sales
              </el-link>
            </div>
          </div>
          <div class="home-main_picture1__connet_pic">
            <picture>
              <source
                srcset="
                  https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.webp
                "
                type="image/webp"
              />
              <img
                src="https://github.githubassets.com/images/modules/site/home/enterprise-city-w-logos.jpg"
                class="
                  width-full
                  height-auto
                  position-absolute
                  right-0
                  bottom-0
                "
                alt="Futuristic city scape"
                loading="lazy"
                decoding="async"
                width="688px"
                height="218px"
              />
            </picture>
          </div>
        </div>
      </div>
    </el-main>
    <el-footer>I'm studying now,xx!</el-footer>
  </el-container>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
  methods: {
    handleSelect(index, indexPath) {
      console.log("index", index);
      console.log("indexPath", indexPath);
    },
  },
};
</script>
<style scoped>
.sign-page_sty {
  width: 100vw;
  height: 100vh;
}
.home-main_picture {
  width: 100%;
  display: flex;
  justify-content: center;
}
.home-main_picture1__connet {
  width: 1080px;
  display: flex;
  justify-content: space-between;
  border-width: 1px;
  border-style: solid;
  border-color: #d0d7de;
  border-radius: 6px;
  box-shadow: 0 22px 17px rgb(0 0 0 / 10%), 0 10px 17px rgb(0 0 0 / 2%) inset;
}
.home-main_picture1__connet :hover {
  box-shadow: 0 22px 17px rgb(0 0 0 / 5%);
}
.home-main_picture1__connet_title {
  padding: 40px 40px 0 40px;
  text-align: left;
  color: #627597;
}
.home-main_picture1__connet_pic {
  position: relative;
  right: 0;
  bottom: -6px;
}
</style>
