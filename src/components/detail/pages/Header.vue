<template>
  <div>
    <div class="back iconfont" @click="back" v-show="showHeader">&#xe60e;</div>
    <div class="headerFixed" v-show="!showHeader" :style="opacityStyle">
      <router-link tag="span" to="/" class="iconfont back2">&#xe60e;</router-link>大连圣亚海洋世界
    </div>
    <div style="height:900px"></div>
  </div>
</template>

<script>
export default {
  name: "",

  data() {
    return {
      showHeader: true,
      opacityStyle: {
        opacity: 0
      }
    };
  },
  activated() {
    window.addEventListener("scroll", this.handleHeader);
  },
  deactivated() {
    window.removeEventListener("scroll", this.handleHeader);
  },
 
  methods: {
    back() {
      this.$emit("back");
    },
    handleHeader() {
      const top = document.documentElement.scrollTop;
      if (top > 0) {
        let opacity = top / 100;
        opacity = opacity > 1 ? 1 : opacity;
        this.opacityStyle = { opacity };
        this.showHeader = false;
      } else {
        this.showHeader = true;
      }
    }
  }
};
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus';

.back {
  font-size: 0.28rem;
  color: #fff;
  width: 0.36rem;
  line-height: 0.36rem;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.5);
  text-align: center;
  position: absolute;
  top: 0;
  margin: 0.04rem;
  z-index: 9;
}

.headerFixed {
  font-size: 0.16rem;
  line-height: 0.44rem;
  text-align: center;
  background: $bgColor;
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;

  .back2 {
    font-size: 0.28rem;
    position: absolute;
    left: 0.1rem;
    top: 0;
  }
}
</style>
