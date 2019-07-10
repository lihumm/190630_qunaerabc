<template>
  <div>
    <div class="banner" @click="showGalleryMethod">
      <img src="@/assets/img/detail06.jpg" alt />
      <div class="banner_title">大连圣亚海洋世界(AAAA景区)</div>
      <div class="imgNum iconfont">&#xe648; 36</div>
    </div>
    <common-gallery :imgs="imgs" v-show="showGallery" @close="closeGalleryMethod"></common-gallery>
  </div>
</template>

<script>
import CommonGallery from "common/gallery/Gallery";
export default {
  name: "DetailBanner",
  components: {
    CommonGallery,
  },
  data() {
    return {
      showGallery: false,
      imgs: [
        "http://img1.qunarzz.com/sight/p0/201404/23/04b92c99462687fa1ba45c1b5ba4ad77.jpg_350x240_4dd46cd0.jpg",
        "http://img1.qunarzz.com/sight/p0/1709/76/7691528bc7d7ad3ca3.img.png_350x240_8d02892d.png"
      ]
    };
  },

  methods: {
    showGalleryMethod() {
      this.showGallery = true;
    },
    closeGalleryMethod() {
      this.showGallery = false;
    },
    
  }
};
</script>

<style lang='stylus' scoped>
.banner {
  overflow: hidden;
  height: 0;
  width: 100%;
  padding-bottom: 55%;
  position: relative;

  img {
    width: 100%;
  }

  .banner_title {
    position: absolute;
    bottom: 0;
    font-size: 0.18rem;
    color: white;
    padding: 0.1rem;
    width: 100%;
    background: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8)); /* 标准的语法 */
  }

  .imgNum {
    width: 0.6rem;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 0.1rem;
    color: white;
    font-size: 0.12rem;
    position: absolute;
    bottom: 0.32rem;
    margin-left: 0.1rem;
    text-align: center;
    line-height: 0.2rem;
  }
}
</style>
