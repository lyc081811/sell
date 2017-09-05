<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li v-for="item in goods" class="menu-item">
          <span class="text border-1px">
            <span class="icon" v-show="item.type>0" :class="classMap[item.type]"></span>
            {{item.name}}
          </span>
        </li>
      </ul>
    </div>
    <div class="foods-wrapper">
      <ul>
        <li v-for="item in goods" class="food-list">
          <h1 class="title">{{item.name}}</h1>
          <ul class="">
            <li v-for="food in item.foods" class="food-item">
              <div class="icon">
                <img :src="food.icon" >
              </div>
              <div class="content">
                <h2 class="name">{{good.name}}</h2>
                <p class="desc">{{food.description}}</p>
                <div class="extra">
                  <span>{{food.sellCount}}</span>
                  <span>好评率{{food.rating}}%</span>
                </div>
                <div class="price">
                  <span>${{food.price}}</span>
                  <span v-show="food.oldPrice">{{food.oldPrice}}</span>
                </div>
              </div>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        goods: []
      };
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
      this.$http.get('/api/goods').then(data => {
        data = data.body;
        if (data.errno === 0) {
          this.goods = data.data;
        }
      });
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import "../../common/stylus/mixin";
.goods
  display flex
  position absolute
  top 174px
  width 100%
  bottom 46px
  overflow hidden
  .menu-wrapper
    flex 0 0 80px
    width 80px
    background-color #f3f5f7
    .menu-item
      display table
      height 54px
      width 56px
      line-height 14px
      padding 0 12px
      .icon
        display inline-block
        vertical-align top
        width 12px
        height 12px
        margin-right 2px
        background-size 12px 12px
        background-repeat no-repeat
        &.decrease
          bg-image('decrease_3')
        &.discount
          bg-image('discount_3')
        &.guarantee
          bg-image('guarantee_3')
        &.invoice
          bg-image('invoice_3')
        &.special
          bg-image('special_3')
      .text
        font-size 12px
        display table-cell
        width 56px
        vertical-align middle
        font-size 12px
        border-1px(rgba(1,17,27,.2))
  .foods-wrapper
    flex 1
</style>
