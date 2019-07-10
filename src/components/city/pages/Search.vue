<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search_input" type="text" placeholder="输入城市名或拼音" />
    </div>
    <div class="search_content" ref="wrapper" v-show="keyword">
      <ul>
        <li v-for="item in list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
import { mapMutations } from "vuex";
export default {
  name: "CitySearch",
  props: {
    alphabetCity: Object
  },
  data() {
    return {
      keyword: "",
      list: [],
      timer: null
    };
  },
  computed: {
    hasNoData() {
      return !this.list.length;
    }
  },
  watch: {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      if (!this.keyword) {
        this.list = [];
        return;
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.alphabetCity) {
          this.alphabetCity[i].forEach(value => {
            if (
              value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1
            ) {
              result.push(value);
            }
          });
        }
        this.list = result;
      }, 100);
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper);
  },
  methods: {
    // handleCityClick(city){
    //   this.$store.commit('changeCity',city)
    //   // this.keyword=''
    //   this.$router.push('/')
    // }
    handleCityClick(city) {
      // this.$store.commit("changeCity", city);
      this.changeCity(city);
      this.keyword = "";
      this.$router.push("/");
    },
    ...mapMutations(["changeCity"])
  }
};
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus';

.search {
  height: 0.34rem;
  background: $bgColor;
  position: relative;
  padding: 0 0.1rem;

  .search_input {
    // width: 3.55rem;
    width: 95%;
    position: absolute;
    top: 0;
    text-align: center;
    height: 0.24rem;
    border-radius: 0.06rem;
    color: #666;
  }
}

.search_content {
  overflow: hidden;
  position: absolute;
  top: 0.78rem;
  left: 0;
  right: 0;
  bottom: 0;
  background: #fff;
  z-index: 1;

  li {
    line-height: 0.3rem;
    padding-left: 0.1rem;
  }
}
</style>
