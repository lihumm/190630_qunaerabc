<template>
  <div>
    <city-header></city-header>
    <city-search :alphabetCity="alphabetCity"></city-search>
    <city-list :hotCity="hotCity" :alphabetCity="alphabetCity" :letter="letter"></city-list>
    <city-Alphabet :alphabetCity="alphabetCity" @change="handleLetterChange"></city-Alphabet>
  </div>
</template>

<script>
import axios from "axios";
import CityHeader from "./pages/CityHeader";
import CitySearch from "./pages/Search";
import CityList from "./pages/List";
import CityAlphabet from "./pages/Alphabet";
export default {
  name: "City",
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data() {
    return {
      hotCity: [],
      alphabetCity:{},
      letter:''
    };
  },
  mounted() {
    this.getCityInfo();
  },

  methods: {
    getCityInfo() {
      axios.get("/api/city.json").then(res => {
        console.log(res);
        res = res.data
        if(res.ret &&res.data != ''){
          this.hotCity = res.data.hotCities
          this.alphabetCity = res.data.cities
        }
      });
    },

    handleLetterChange(letter){
        this.letter = letter
      }
  }
  
};
</script>

<style lang='stylus' scoped></style>
