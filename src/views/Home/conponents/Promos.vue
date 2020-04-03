<template>
  <div class="all">
    <div class="promos">
      <div class="promo" ref="bottomone">
        <div>
          <img src="../../../assets/images/promo-one.jpg" >
        </div>
        <div class="font" :class="{byron: isByron[0]}">
          <div>媒体</div>
          <div>OnePlus 7T 系列获全球多家媒体好评</div>
          <div>了解更多</div>
        </div>
      </div>
      <div class="promo" ref="bottomtwo">
        <div>
          <img src="../../../assets/images/promo-two.jpg" >
        </div>
        <div class="font" :class="{byron: isByron[1]}">
          <div>故事</div>
          <div>「美无边界 动则有灵」OnePlus 壁纸背后的故事</div>
          <div>了解更多</div>
        </div>
      </div>
      <div class="promo" ref="bottomthree">
        <div>
          <img src="../../../assets/images/promo-three.jpg" >
        </div>
        <div class="font" :class="{byron: isByron[2]}">
          <div>报告</div>
          <div>「旦用难回」OnePlus 90Hz 实验报告首发</div>
          <div>了解更多</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.all{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
  padding: 5% 0;
  background: #f6f6f6;
}
.promos{
  width: 1300px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  .promo{
    @media screen and (max-width: 1180px){
      width: 100%;
      padding: 20px 40px;
    }
    img{
      width: 100%;
      &:hover{
        box-shadow: 0px 2px 5px rgba(185,185,191,.4);
        transform: translateY(-5px);
        transition: transform .5s;
      }
    }
    .font{
      margin-top: 20px;
      transform: scale(1.02);
      transition: all .25s;
      div:first-of-type {
        font-size: 16px;
      }
      div:nth-of-type(2){
        font-size: 18px;
        margin-top: 5px;
      }
      div:nth-of-type(3){
        font-size: 16px;
        color: #09c;
        margin-top: 20px;
      }
    }
  }
}
.all .promos .promo .byron{
  transform: scale(1);
}
</style>

<script>
export default {
  name: 'HomePromos',
  data () {
    return {
      bottom: [],
      isByron: [false, false, false]
    }
  },
  methods: {
    getBottom () {
      this.bottom[0] = Math.floor((this.$refs.bottomone.offsetTop) - 600)
      this.bottom[1] = Math.floor((this.$refs.bottomtwo.offsetTop) - 600)
      this.bottom[2] = Math.floor((this.$refs.bottomthree.offsetTop) - 600)
    },
    getScroll () {
      console.log(document.documentElement.scrollTop)
      for (let i = 0; i < this.bottom.length; i++) {
        if (this.bottom[i] < document.documentElement.scrollTop) {
          this.$set(this.isByron, i, true)
        } else {
          this.$set(this.isByron, i, false)
        }
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.getScroll)
    this.getBottom()
  }
}
</script>
