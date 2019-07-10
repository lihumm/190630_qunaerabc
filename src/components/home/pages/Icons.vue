<template>
  <div>
    <div class="icons">
      <swiper :options="swiperOption" v-if="iconsListLength">
        <swiper-slide v-for="(page,index) in pages" :key="index">
          <div class="icon_list" v-for="item in page" :key="item.id">
            <div class="icon_list_img">
              <img :src="item.imgUrl">
            </div>
            <p>{{item.desc}}</p>
          </div>
        </swiper-slide>

        <!-- Optional controls -->
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
    <div class="categories">
      <div class="categories_left"><span class="iconfont">&#xe61f;</span> 定位失败</div>

      <div class="categories_right"><span class="iconfont">&#xe642;</span> 必游榜单</div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "",
  props:{
    iconsList:Array
  },
  data() {
    return {
      // iconList: [
      //   {
      //     id: "1",
      //     iconUrl: require("@/assets/img/icon01.png"),
      //     title: "景点门票"
      //   },
      //   {
      //     id: "2",
      //     iconUrl: require("@/assets/img/icon02.png"),
      //     title: "6月特惠"
      //   },
      //   {
      //     id: "3",
      //     iconUrl: require("@/assets/img/icon03.png"),
      //     title: "深圳必游"
      //   },
      //   {
      //     id: "4",
      //     iconUrl: require("@/assets/img/icon04.png"),
      //     title: "海洋馆"
      //   },
      //   {
      //     id: "5",
      //     iconUrl: require("@/assets/img/icon05.png"),
      //     title: "广州融创"
      //   },
      //   {
      //     id: "6",
      //     iconUrl: require("@/assets/img/icon06.png"),
      //     title: "深圳动物园"
      //   },
      //   {
      //     id: "7",
      //     iconUrl: require("@/assets/img/icon07.png"),
      //     title: "世界之窗"
      //   },
      //   {
      //     id: "8",
      //     iconUrl: require("@/assets/img/icon08.png"),
      //     title: "东部华侨城"
      //   },
      //   {
      //     id: "9",
      //     iconUrl: require("@/assets/img/icon09.png"),
      //     title: "世界之窗"
      //   },
      //   {
      //     id: "10",
      //     iconUrl: require("@/assets/img/icon10.png"),
      //     title: "东部华侨城"
      //   }
      // ],
      swiperOption: {
        pagination: ".swiper-pagination",
        loop: true
      }
    };
  },
  computed: {
    pages() {
      const pages = [];
      this.iconsList.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    },
    iconsListLength(){
      return this.iconsList.length
    }
  },
  methods: {}
};
</script>

<style lang="stylus" scoped>
@import '~css/common.stylus';

.categories {
  background #fff
  text-align center
  font-size: 0.14rem;
  line-height: 0.48rem;
  display: flex;
  justify-content: space-between;
  .categories_left{
    flex 1
    border-right 1px #f8f8f8 solid;
  }
  .categories_right{
    flex 1
  }
}

.icons {
  background #fff
  border-bottom: 1px #f8f8f8 solid;
  overflow: hidden;
  margin-top: -0.05rem;
  height: 1.85rem;
  position: relative;
}

.icon_list {
  padding: 0.1rem 0 0;
  width: 25%;
  float: left;
  height: 0.75rem;
  text-align: center;
  position: relative;
}

.icon_list:nth-child(8) {
  margin-bottom: 20px;
}

.icon_list_img {
  position: relative;
  margin: 0 auto;
  height: 0.55rem;
  width: 0.55rem;
}

.icon_list_img img {
  position: absolute;
  top: 0;
  left: 0;
  height: 0.55rem;
  width: 0.55rem;
}

.icon_list p {
  padding: 0.05rem 0 0;
  font-size: 0.14rem;
  ellipsis();
}

.icons >>> .swiper-pagination {
  position: absolute;
  overflow: visible;
}

.icons >>> .swiper-pagination-bullet {
  color: #33bfcb;
  width: 0.06rem;
  height: 0.06rem;
}

.icons >>> .swiper-pagination-bullet-active {
  background: #33bfcb;
}
</style>
