<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="list_item">
        <div class="title border">您的位置</div>
        <div class="city">
          <router-link to="/">
            <div class="button_box">
              <button class="city_button">{{this.currentCity}}</button>
            </div>
          </router-link>
        </div>
      </div>
      <div class="list_item">
        <div class="title">热门城市</div>
        <div class="city">
          <div
            class="button_box"
            v-for="item in hotCity"
            :key="item.id"
            @click="handleCityClick(item.name)"
          >
            <button class="city_button">{{ item.name }}</button>
          </div>
        </div>
      </div>

      <div class="list_item" v-for="(item,key) in alphabetCity" :key="key" :ref="key">
        <div class="title">{{key}}</div>
        <div
          class="bottom_city"
          v-for="innerItem in item"
          :key="innerItem.id"
          @click="handleCityClick(innerItem.name)"
        >{{ innerItem.name }}</div>
      </div>
      <!-- <div class="list_item">
        <div class="title">B</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
      </div>
      <div class="list_item">
        <div class="title">C</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
      </div>
      <div class="list_item">
        <div class="title">D</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
        <div class="bottom_city">阿拉尔</div>
      </div>-->
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
import { mapState, mapMutations } from "vuex";
export default {
  name: "CityList",
  props: {
    hotCity: Array,
    alphabetCity: Object,
    letter: String
  },
  data() {
    return {};
  },
  computed: {
    //我把vuex里的city这个公用的数据,映射到我这个组件的conputed计算属性里,映射过来的名字叫做currentCity
    ...mapState({
      currentCity: "city"
    })
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper);
  },
  methods: {
    handleCityClick(city) {
      // this.$store.commit("changeCity", city);
      this.changeCity(city);
      this.$router.push("/");
    },
    ...mapMutations(["changeCity"])
  },
  watch: {
    letter() {
      if (this.letter) {
        const element = this.$refs[this.letter][0];
        this.scroll.scrollToElement(element);
      }
    }
  }
};
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus';

.list {
  font-size: 0.12rem;
  overflow: hidden;
  position: absolute;
  left: 0;
  top: 0.78rem;
  right: 0;
  bottom: 0;

  .list_item {
    .title {
      line-height: 0.38rem;
      padding-left: 0.15rem;
      color: #212121;
    }

    // .border {
    // &:before {
    // border: 1px solid red;
    // }

    // &:after {
    // border: 1px solid red;
    // }
    // }
    .city {
      padding-left: 0.1rem;
      padding-bottom: 0.1rem;
      background: #fff;
      font-size: 0.14rem;
      line-height: 0.28rem;

      .button_box {
        margin: 0.1rem 0.02rem 0;
        display: inline-block;

        .city_button {
          height: 0.28rem;
          width: 1rem;
          background: #fff;
          font-weight: bold;
          color: #212121;
          border: 0.01rem solid #d8d8d7;
          border-radius: 0.04rem;
        }
      }
    }

    .bottom_city {
      font-weight: bold;
      padding-left: 0.1rem;
      background: #fff;
      line-height: 0.3rem;
      border-bottom: 0.01rem solid $borderBottom;
    }
  }
}
</style>
