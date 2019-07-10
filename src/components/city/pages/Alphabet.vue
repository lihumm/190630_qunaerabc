<template>
  <div class="alphabet_box">
    <ul class="alphabet">
      <li v-for="(item,key) in alphabetCity" :key="key" @click="handleLetterClick">{{key}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "",
  props: {
    alphabetCity: Object
  },
  data() {
    return {};
  },

  methods: {
    handleLetterClick(e){
      this.$emit('change',e.target.innerText)
    }
  }
};
</script>

<style lang='stylus' scoped>
@import '~css/common.stylus';

.alphabet_box {
  .alphabet {
    position: absolute;
    top: 0;
    right: 0;
    height: 100%;
    width: 0.4rem;
    display: flex;
    flex-direction: column;
    justify-content: center;

    li {
      line-height: 0.2rem;
      text-align: center;
      color: $bgColor;
    }
  }
}
</style>
