<template>
  <div class="cityHeader">
    <router-link to="/">
      <span class="iconfont header-back">&#xe60e;</span>
    </router-link>城市选择
  </div>
</template>

<script>
export default {
  name: "CityHeader",

  data() {
    return {};
  },

  methods: {}
};
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus';

.cityHeader {
  background: $bgColor;
  text-align: center;
  font-size: 0.16rem;
  line-height: 0.44rem;
  color: #fff;
  position: relative;

  a {
    color: #fff;

    span {
      position: absolute;
      left: 0.1rem;
      font-size: 0.2rem;
    }
  }
}
</style>
