<template>
  <div class="footer">
    <div class="footer_top">
      <ul>
        <li>
          <a href="#">
            <div class="iconfont">&#xe642; </div><span class="text">机票</span>
          </a>
        </li>
        <li>
          <a href="#">
            <div class="iconfont">&#xe642;</div><span class="text">酒店</span>
          </a>
        </li>
        <li>
          <a href="#">
            <div class="iconfont">&#xe642;</div><span class="text">公寓</span>
          </a>
        </li>
        
        <li>
          <a href="#">
            <div style="float:left;padding-right:.1rem">|</div><div class="iconfont">&#xe642; </div><span class="text">更多</span>
          </a>
        </li>
      </ul>
    </div>
    <div class="footer_middle">
      <ul>
        <li>
          <a href="#">
            <span>登陆</span>
          </a>
        </li>
        <li>
          <a href="#">
            <span>我的订单</span>
          </a>
        </li>
        <li>
          <a href="#">
            <span>最近浏览</span>
          </a>
        </li>
        <li>
          <a href="#">
            <span>关于我们</span>
          </a>
        </li>
      </ul>
    </div>
    <div class="footer_bottom">
      <span class="span_left">触控板</span><span class="span_right">电脑板</span>
      <p>Qunar 京ICP备05021087 意见反馈</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "",

  data() {
    return {};
  },

  methods: {}
};
</script>

<style lang='stylus' scoped>
.footer {
    
  height: 1.33rem;
  font-size: 0.14rem;
  color: #9e9e9e;
  .footer_top{
      font-size .12rem
      ul{
        display flex
        flex-direction row
        justify-content center
        padding .1rem .1rem 0
        li{
            width .65rem
            height .25rem
            padding-left .1rem
            text-align center
            a{
                color #acacac
            }
            .iconfont {
                font-size .22rem
                float left
            }
            .text{
                padding-bottom .02rem
                border-bottom .01rem solid #acacac
                
            }
        }
      }
  }
  .footer_middle{
      border-bottom .01rem solid #cacaca
      line-height .39rem
      ul{
          display flex
          justify-content flex-start
          li{
              padding-left .2rem
              a{
                  color #25a4bb
              }
          }
      }
  }
  .footer_bottom{
    text-align center
    padding-top .1rem 
    .span_left{
      color #000
    }
    .span_right{
      color #25a4bb
      padding-left .2rem
    }
    p{
      padding .1rem
    }
  }
}
</style>
