<template>
  <div>
    <div class="header">
      <div class="header-left">
        <span class="iconfont">&#xe60e;</span>
      </div>
      <div class="header-search">
        <span class="iconfont">&#xe873;</span>输入城市/景点/游玩主题
      </div>
      <div class="header-right">
        <router-link to="/city">
          <!-- {{this.$store.state.city}} -->
          {{this.city}}
          <span class="iconfont">&#xe627;</span>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: "HomeHeader",
  computed:{
    //我把vuex里面的数据映射到当前组件的computed属性里.映射什么呢?(我把city这个公用数据映射到我这个名字叫做city的计算属性当中/映射过来的名字叫做city)
    //这样上面就可以不用写this.$store.state.city了,直接用this.city即可
    ...mapState(['city'])  //传递的是一个数组,也可以是一个对象
  },
  components:{
  },
 
  data() {
    return {};
  },

  methods: {}
};
</script>

<style lang="stylus" scoped>
@import '~css/common.stylus';

.header {
  color: white;
  height: 0.44rem;
  line-height: 0.44rem;
  background: $bgColor;
  display: flex;
  font-size: 0.18rem;

  .header-left {
    width: 0.2rem;
    padding: 0 0.1rem;

    span {
      font-size: 0.2rem;
    }
  }

  .header-search {
    flex: 1;
    height: 0.3rem;
    line-height: 0.3rem;
    margin: 0.06rem;
    background: #fff;
    border-radius: 0.05rem;
    color: #e4e5e8;
    font-size: 0.14rem;
    padding-left: 0.1rem;
  }

  .header-right {
    font-size: 0.14rem;
    padding: 0 0.1rem;
    a{
        color #fff
    }
  }
}
</style>
