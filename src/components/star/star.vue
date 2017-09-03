<template>
    <div class="start" :class="starType">
        <span v-for="itemClass in itemClasses" :class="itemClasses"  class="start-item"></span>
    </div>
</template>

<script>
  export default {
      props: {
          size: {
              type: Number
          },
          store: {
              type: Number
          }
      },
      computed: {
          starType() {
              return 'star-'+this.size
          }
      }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .star
         .star-item
            display block
            background-repeat no-repeat
        &.star-48
            .star-item
                width 20px
                height 20px
                
        &.star-36
        &.star-24
       
</style>
