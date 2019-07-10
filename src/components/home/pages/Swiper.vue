<template>
  <div class="swiper">
    <swiper :options="swiperOption" v-if="swiperList.length">
      <!-- slides -->
      <swiper-slide v-for="item in swiperList" :key="item.id">
        <img :src="item.imgUrl" alt>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "",
  props:{
    swiperList:Array
  },
  data() {
    return {
      // swiperList: [
      //   {
      //     id: "1",
      //     imgUrl: require("@/assets/img/swipe01.jpg")
      //   },
      //   {
      //     id: "2",
      //     imgUrl: require("@/assets/img/swipe02.jpg")
      //   },
      //   {
      //     id: "3",
      //     imgUrl: require("@/assets/img/swipe03.jpg")
      //   }
      // ],
      swiperOption: {
        pagination: ".swiper-pagination",
        loop: true,
        autoplay:4000,
      }
    };
  },

  methods: {}
};
</script>

<style lang='stylus' scoped>
.swiper {
  background #fff
  img {
    
    height: 100%;
    width: 100%;
  }

  color: white;

 

  >>> .swiper-pagination-bullet-active {
    background: #fff;
  }
}
</style>
