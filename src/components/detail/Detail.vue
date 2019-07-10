<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header @back="back"></detail-header>

  </div>
</template>

<script>
import DetailBanner from './pages/Banner'
import DetailHeader from "./pages/Header";

export default {
  name: 'Detail',
  components:{
    DetailBanner,
    DetailHeader
  },
  data () {
    return {
    }
  },

  methods: {
    back(){
      this.$router.push('/')
    }
  }
}
</script>

<style lang='stylus' scoped>

</style>
