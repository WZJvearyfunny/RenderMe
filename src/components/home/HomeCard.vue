<template>
  <div class="home-main_picture">
    <div class="home-main_picture1__connet" ref="connet">
      <div class="home-main_picture1__connet_title" style="max-width: 310px">
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
            {{ hdec }}
          </h2>
        </label>
        <label>
          <p>
            {{ pdec }}
          </p>
        </label>
        <div>
          <div
            class="home-main_picture1__connet_title_buttonlist"
            v-for="(item, index) in buttonList"
            :style="{ marginTop: index > 0 ? '10px' : '' }"
            v-bind:key="index"
          >
            <el-button @click="applyFn(item.titleFn)">
              {{ item.title }}
            </el-button>
            <el-link type="primary"> {{ item.contact }} </el-link>
          </div>
        </div>
      </div>
      <div class="home-main_picture1__connet_pic">
        <picture>
          <source :srcset="imgsrcset" type="image/webp" />
          <img
            :src="imgsrc"
            class="width-full height-auto position-absolute right-0 bottom-0"
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
</template>

<script>
export default {
  name: "HomeCard",
  props: {
    hdec: {
      type: String,
    },
    pdec: {
      type: String,
    },
    imgsrc: {
      type: String,
      require: true,
    },
    imgsrcset: {
      type: String,
      require: true,
    },
    buttonList: {
      type: Array,
    },
  },
  mounted() {},
  methods: {
    applyFn(fn) {
      this.$emit(fn, "0");
    },
  },
};
</script>

<style scoped>
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
.home-main_picture1__connet_title_buttonlist {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-column-gap: 20px;
}
</style>
