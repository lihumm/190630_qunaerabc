<template>
  <div class="like">
    <div class="like_head">
      <span>❤</span>猜你喜欢
    </div>
      <router-link tag="div" :to="'/detail/'+ item.id" class="like_content" v-for="item in likeList" :key="item.id">
        <div class="like_content_left">
          <img :src="item.imgUrl" alt />
        </div>
        <div class="like_content_right">
          <p class="title">{{item.title}}</p>
          <div class="comment">
            {{item.star}}
            <span>{{item.comment}}条评论</span>
          </div>
          <div class="price">
            <em>
              <i>￥</i>
              {{item.price}}
            </em>起
            <span>{{item.place}}</span>
          </div>
          <div class="desc">{{item.desc}}</div>
        </div>
    </router-link>
    <!-- 查看所有产品 -->
    <div class="like_readAll">查看所有产品</div>
  </div>
</template>

<script>
export default {
  name: "Like",

  data() {
    return {
      likeList: [
        {
          id: "1",
          imgUrl: require("@/assets/img/hotList_item06.jpg"),
          title: "大连圣亚海洋世界",
          star: "⭐⭐⭐⭐⭐",
          comment: "43574",
          price: "69.9",
          place: "华侨城",
          desc: "国际比纠结清凉一夏，夜场49.9元"
        },
        {
          id: "2",
          imgUrl: require("@/assets/img/hotList_item03.jpg"),
          title: "深圳欢乐谷",
          star: "⭐⭐⭐⭐",
          comment: "5741",
          price: "84",
          place: "南山区",
          desc: "玛雅水公园，夏日玩水好去处"
        },
        {
          id: "3",
          imgUrl: require("@/assets/img/hotList_item02.jpg"),
          title: "深圳小梅沙海洋世界",
          star: "⭐⭐⭐⭐⭐",
          comment: "16951",
          price: "69.9",
          place: "小梅沙",
          desc: "一天穿越四大洋"
        },
        {
          id: "4",
          imgUrl: require("@/assets/img/hotList_item04.jpg"),
          title: "深圳野生动物园",
          star: "⭐⭐⭐⭐⭐",
          comment: "43574",
          price: "99",
          place: "南山区",
          desc: "6.29-6.30周末有特惠99.9元/人"
        }
      ]
    };
  },

  methods: {}
};
</script>

<style lang='stylus' scoped>
.like {
  margin-top: 0.1rem;
  padding: 0.1rem 0.1rem 0;
  background: #fff;
  font-size: 0.16rem;

  .like_head {
    line-height: 0.47rem;

    span {
      color: #ff5b58;
    }
  }

  .like_content {
    border-bottom: 1px solid #f5f5f5;
    background: #fff;
    font-size: 0.12rem;
    padding: 0.1rem 0;
    height: 1.38rem;
    display: flex;

    .like_content_left {
      margin-right: 0.1rem;

      img {
        width: 1rem;
      }
    }

    .like_content_right {
      flex-direction: columns;
      position: relative;
      flex: 1;

      .title {
        margin-top: 0.15rem;
        font-size: 0.16rem;
      }

      .comment {
        margin-top: 0.09rem;
        font-size: 0.12rem;
      }

      .price {
        margin-top: 0.13rem;
        color: #616161;

        em {
          color: #ff8300;
          font-size: 0.2rem;

          i {
            font-size: 0.12rem;
          }
        }

        span {
          float: right;
          right: 0.1rem;
        }
      }

      .desc {
        position: absolute;
        bottom: 0;
        font-size: 0.12rem;
        background: #fff9f9;
        color: #ff5555;
      }
    }
  }

  .like_readAll {
    line-height: 0.4rem;
    font-size: 0.14rem;
    text-align: center;
    color: #00AFC7;
  }
}
</style>
