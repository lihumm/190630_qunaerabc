<template>
  <div>
    <p class="weekend_title">周末去哪儿</p>
    <div class="weekend_content">
        <div class="weekend_content_item" v-for="item in weekendList" :key="item.id">
            <img :src="item.imgUrl" alt="">
            <p class="title">
                {{item.title}}
            </p>
            <p class="desc">
                {{item.desc}}
            </p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: '',
  props:{
    weekendList:Array
  },
  data () {
    return {
      //   weekendList: [
      //   {
      //     id: "1",
      //     imgUrl: require("@/assets/img/weekend01.jpg"),
      //     title: "世界之窗",
      //     desc: "国际比纠结清凉一夏，夜场49.9元国际比纠结清凉一夏，夜场49.9元国际比纠结清凉一夏，夜场49.9元国际比纠结清凉一夏，夜场49.9元"
      //   },
      //   {
      //     id: "2",
      //     imgUrl: require("@/assets/img/weekend02.jpg"),
      //     title: "世界之窗",
      //     desc: "国际比纠结清凉一夏，夜场49.9元"
      //   },
      //   {
      //     id: "3",
      //     imgUrl: require("@/assets/img/weekend01.jpg"),
      //     title: "世界之窗",
      //     desc: "国际比纠结清凉一夏，夜场49.9元"
      //   },
      //   {
      //     id: "4",
      //     imgUrl: require("@/assets/img/weekend02.jpg"),
      //     title: "世界之窗",
      //     desc: "国际比纠结清凉一夏，夜场49.9元国际比纠结清凉一夏，夜场49.9元 "
      //   },
      // ]
    }
  },

  methods: {}
}
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus'
.weekend_title{
    line-height .4rem
    font-size .14rem
    padding-left .1rem
}
.weekend_content_item{
    &.weekend_content_item:nth-child(1){
        margin-top 0
    }
    margin-top .06rem
    height 2.03rem
    font-size .14rem
    background-color #fff
    img{
        width 100%
        height 1.375rem
    }
    .title{
        padding .1rem 
    }
    .desc{
        ellipsis()
        padding 0 .7rem 0 .1rem
        font-size .13rem
        color #616161
    }
}
</style>
