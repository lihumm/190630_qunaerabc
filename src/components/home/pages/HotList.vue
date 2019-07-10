<template>
  <div class="hotList">
    <!-- 热门榜单头部 -->
    <div class="hotList_head">
      <div class="hotList_head_left">
        <p>
          <span class="iconfont" style="color:#ff8244">&#xe648;</span>本周热门榜单
        </p>
      </div>
      <div class="hotList_head_right">
        <p>
          全部榜单
          <span class="iconfont">&#xe610;</span>
        </p>
      </div>
    </div>
    <!-- 热门榜单列表 -->
    <div class="hotList_content">
      <div class="hotList_content_items" v-for="item in hotList" :key="item.id">
        <img class="imgUrl" :src="item.imgUrl">
        <img class="imgTop" :src="item.imgTop">
        <p>{{item.title}}</p>
        <span>
          <em>${{item.money}}</em> 起
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HotList",

  data() {
    return {
      hotList: [
        {
          id: "1",
          imgUrl: require("@/assets/img/hotList_item01.jpg"),
          imgTop: require("@/assets/img/top1.png"),
          title: "世界之窗",
          money: "69"
        },
        {
          id: "2",
          imgUrl: require("@/assets/img/hotList_item02.jpg"),
          imgTop: require("@/assets/img/top2.png"),
          title: "东部华侨城大峡谷",
          money: "150"
        },
        {
          id: "3",
          imgUrl: require("@/assets/img/hotList_item03.jpg"),
          imgTop: require("@/assets/img/top3.png"),
          title: "深圳欢乐谷",
          money: "84"
        },
        {
          id: "4",
          imgUrl: require("@/assets/img/hotList_item04.jpg"),
          imgTop: '',
          title: "深圳小梅沙",
          money: "69"
        },
        {
          id: "5",
          imgUrl: require("@/assets/img/hotList_item05.jpg"),
          imgTop: '',
          title: "世界之窗",
          money: "69"
        },
        {
          id: "6",
          imgUrl: require("@/assets/img/hotList_item01.jpg"),
          imgTop: '',
          title: "世界之窗",
          money: "69"
        },
        {
          id: "7",
          imgUrl: require("@/assets/img/hotList_item02.jpg"),
          imgTop: '',
          title: "世界之窗",
          money: "69"
        },
        {
          id: "8",
          imgUrl: require("@/assets/img/hotList_item03.jpg"),
          imgTop: '',
          title: "世界之窗",
          money: "69"
        }
      ]
    };
  },

  methods: {}
};
</script>

<style lang='stylus' scoped>
.hotList {
  margin-top: 0.1rem;
  background: #fff;
  padding: 0 0.1rem;
  font-size: 0.12rem;
  height: 2rem;

  .hotList_head {
    line-height: 0.47rem;
    display: flex;
    justify-content: space-between;

    .hotList_head_left {
      font-size: 0.16rem;
      flex: 1;
    }

    .hotList_head_right {
      color: #616161;
      text-align: right;
      flex: 1;
    }
  }

  .hotList_content {
    overflow: auto;
    width: 100%;
    height: 1.6rem;
    display: flex;

    .hotList_content_items {
      position: relative;
      padding-top .05rem
      margin-right: 0.05rem;
      text-align: center;
      width: 1rem;
      height: 1.48rem;

      .imgUrl {
        width: 1rem;
      }

      .imgTop {
        border-radius .02rem
        width: 0.42rem;
        position: absolute;
        left: 0;
        top: .02rem;
        z-index: 999;
      }

      p {
        margin: 0.05rem 0;
      }

      span {
        color: #616161;
      }

      em {
        color: #ff8300;
      }
    }
  }
}
</style>
