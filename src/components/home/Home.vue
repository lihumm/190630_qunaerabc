<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconsList="iconsList"></home-icons>
    <hot-list></hot-list>
    <Like></Like>
    <Weekend :weekendList="weekendList"></Weekend>
    <Footer></Footer>
  </div>
</template>

<script>
import HomeHeader from "../home/pages/Header";
import HomeSwiper from "../home/pages/Swiper";
import HomeIcons from "../home/pages/Icons";
import HotList from "../home/pages/HotList";
import Like from "../home/pages/Like";
import Weekend from "../home/pages/Weekend";
import Footer from "../home/pages/Footer";
import { mapState } from "vuex";
import axios from "axios";
export default {
  name: "Home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HotList,
    Like,
    Weekend,
    Footer
  },
  data() {
    return {
      lastCity: "",
      swiperList: [],
      iconsList: [],
      weekendList: []
    };
  },
  computed: {
    ...mapState(["city"])
  },
  methods: {
    getHomeInfo() {
      axios.get("/api/index.json?city=" + this.city).then(res => {
        console.log(res);
        res = res.data;
        if (res.ret && res.data) {
          this.swiperList = res.data.swiperList;
          this.iconsList = res.data.iconList;
          this.weekendList = res.data.weekendList;
        }
      });
    }
  },
  mounted() {
    // this.city=this.city
    this.lastCity = this.city;
    this.getHomeInfo();
  },
  activated() {
    if(this.lastCity !== this.city){
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
};
</script>

<style  scoped></style>
