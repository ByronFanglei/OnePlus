<template>
  <div class="four">
    <div class="four-style" ref="bottomone">
      <div class="img one-img" :class="{byron: isByron[0]}">
        <div class="font" :class="{byronFont: isByron[0]}">
          <div class="font-one">以旧换新 </div>
          <div class="font-two">助你轻松购新机</div>
        </div>
      </div>
    </div>
    <div class="four-style" ref="bottomtwo">
      <div class="img two-img" :class="{byron: isByron[1]}">
        <div class="font" :class="{byronFont: isByron[1]}">
          <div class="font-one">OnePlus 2020 春季校园招聘</div>
          <div class="font-two">线上全面开启</div>
        </div>
      </div>
    </div>
    <div class="four-style" ref="bottomthree">
      <div class="img three-img" :class="{byron: isByron[2]}">
        <div class="font font-color" :class="{byronFont: isByron[2]}">
          <div class="font-one">教育用户认证享优惠</div>
          <div class="font-two">了解更多</div>
        </div>
      </div>
    </div>
    <div class="four-style" ref="bottomfour">
      <div class="img four-img" :class="{byron: isByron[3]}">
        <div class="font" :class="{byronFont: isByron[3]}">
          <div class="font-one">零售店体验与购买</div>
          <div class="font-two">了解更多</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.four{
  display: flex;
  width: 100%;
  flex-flow: wrap row;
  justify-content: center;
  padding: 0 5px;
  margin-top: 10px;
  .four-style{
    width: 50%;
    height: 500px;
    box-sizing: border-box;
    max-width: 1270px;
    margin-bottom: 10px;
    padding: 0 5px;
    overflow: hidden;
    @media screen and (max-width: 700px) {
      width: 100%;
    }
    .img{
      transform: scale(1.1);
      width: 100%;
      height: 100%;
      position: relative;
      transition: all 1s cubic-bezier(0.25,0.1, 0.25 ,1);
      .font{
        opacity: 0;
        transform: scale(1.1);
        transition: all 1s cubic-bezier(0.25,0.1, 0.25 ,1);
        position: absolute;
        top: 30px;
        width: 100%;
        text-align: center;
        font-weight: 500;
        .font-one{
          font-size: 30px;
          @media screen and (max-width: 700px) {
            font-size: 20px;
          }
        }
        .font-two{
          font-size: 20px;
          @media screen and (max-width: 700px) {
            font-size: 18px;
          }
        }
      }
      .font-color{
        color: #fff;
      }
    }
    .one-img{
      background: url('../../../assets/images/four-one.jpg') center center no-repeat;
    }
    .two-img{
      background: url('../../../assets/images/four-two.jpg') center center no-repeat;
    }
    .three-img{
      background: url('../../../assets/images/four-three.jpg') center center no-repeat;
    }
    .four-img{
      background: url('../../../assets/images/four-four.jpg') center center no-repeat;
    }
  }
}
.four .four-style .img .byronFont{
  opacity: 1;
  transform: scale(1);
}
.four .four-style .byron{
  transform: scale(1);
}
</style>

<script>
export default {
  name: 'HomeFour',
  data () {
    return {
      bottom: [],
      isByron: [false, false, false, false]
    }
  },
  methods: {
    getBottom () {
      this.bottom[0] = Math.floor((this.$refs.bottomone.offsetTop + (this.$refs.bottomone.offsetHeight / 2)) / 1.8)
      this.bottom[1] = Math.floor((this.$refs.bottomtwo.offsetTop + (this.$refs.bottomtwo.offsetHeight / 2)) / 1.8)
      this.bottom[2] = Math.floor((this.$refs.bottomthree.offsetTop + (this.$refs.bottomthree.offsetHeight / 2)) / 1.8) + 100
      this.bottom[3] = Math.floor((this.$refs.bottomfour.offsetTop + (this.$refs.bottomfour.offsetHeight / 2)) / 1.8) + 100
    },
    getScroll () {
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
