<template>
  <div class="food" v-show="showFlag"></div>
</template>

<script>
  export default {
    props: {
      food: {
        type: Object
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .food
    display fixed
    left 0
    top 0
    bottom 48px
    z-z-index 2
    width 100%
    background-color #fff

</style>