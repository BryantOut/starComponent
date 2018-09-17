<template>
    <div class="star" :class="starType">
        <span class="star-item" v-for='(itemClass,index) in createStarList' :key='index' :class='itemClass'>{{rating}}</span>
    </div>
</template>

<script>
// 定义星星的个数
const LENGTH = 5
// 代表一颗星全亮
const CLS_ON = 'on'
// 代表一颗星半亮
const CLS_HALF = 'half'
// 代表一颗星不亮
const CLS_OFF = 'off'
export default {
  props: {
    rating: {
      type: Number
    },
    size: {
      type: Number
    }
  },
  computed: {
    starType () {
      console.log('star-' + this.size)
      return 'star-' + this.size
    },
    createStarList () {
      var starList = []
      // 对数据进行一个处理要么为整数要么为4.5,3.5等
      var score = Math.floor(this.rating * 2) / 2
      // 是否有半星,true表示有半星，false表示没有半星
      var hasDecimal = score % 1 !== 0
      // 全星个数
      var integer = Math.floor(score)
      // 存放全亮的星星
      for (var i = 0; i < integer; i++) {
        starList.push(CLS_ON)
      }
      // 存放半亮的星星
      if (hasDecimal) {
        starList.push(CLS_HALF)
      }
      // 如果星星状态的个数还没有达到5个，那么剩下的用不亮的星星状态代替
      while (starList.length < LENGTH) {
        starList.push(CLS_OFF)
      }
      console.log(starList)
      return starList
    }
  }
}
</script>

<style scoped lang='stylus'>
.star
    font-size:0
    &.star-48
      .star-item
        display:inline-block
        background-repeat:no-repeat
        width:20px
        height:20px
        margin-right:22px
        background-size:20px 20px
        &:last-child
          margin-right:0
        &.on
          background-image:url('./star48_on@2x.png')
        &.half
          background-image:url('./star48_half@2x.png')
        &.off
          background-image:url('./star48_off@2x.png')
    &.star-36
      .star-item
        display:inline-block
        background-repeat:no-repeat
        width:15px
        height:15px
        margin-right:6px
        background-size:15px 15px
        &:last-child
          margin-right:0
        &.on
          background-image:url('./star36_on@2x.png')
        &.half
          background-image:url('./star36_half@2x.png')
        &.off
          background-image:url('./star36_off@2x.png')
    &.star-24
      .star-item
        display:inline-block
        background-repeat:no-repeat
        width:10px
        height:10px
        margin-right:3px
        background-size:10px 10px
        &:last-child
          margin-right:0
        &.on
          background-image:url('./star24_on@2x.png')
        &.half
          background-image:url('./star24_half@2x.png')
        &.off
          background-image:url('./star24_off@2x.png')
</style>
