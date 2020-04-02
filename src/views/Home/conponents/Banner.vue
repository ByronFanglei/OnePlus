<template>
<div>
  <div class="one">
    <div class="banner-one" ref="offsetone" :class="{byron: isByron[0]}">
      <div class="inner">
        <div class="banner-inner">
          <div class="banner-header">OnePlus 8 系列新品发布会</div>
          <div class="banner-body">肉眼可见的出类拔萃</div>
          <div class="banner-time">4 月 16 日 19:00</div>
          <div class="banner-button">了解新品</div>
        </div>
      </div>
    </div>

    <div class="banner-one banner-two" ref="offsettwo" :class="{byron: isByron[1]}">
      <div class="inner">
        <div class="banner-inner">
          <div class="banner-header">OnePlus 7T</div>
          <div class="banner-body">全系 90Hz，流畅新标杆</div>
          <div class="banner-time">￥2999 起</div>
          <div class="banner-button">立即购买</div>
          <div>了解产品</div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<style lang="scss" scoped>
@import '../../../assets/style/scss/custom.scss';
@import '../../../assets/style/scss/animation.scss';

.one{
  width: 100%;
  background: #000;
  overflow: hidden;
}
.banner-one{
  width: 100%;
  height: 680px;
  background: url('../../../assets/images/banner-one.jpg') center center no-repeat;
  margin-top: 10px;
  position: relative;
  opacity: 0;
  transform: scale(1.1);
  transition: all 1s cubic-bezier(0.25,0.1, 0.25 ,1);
  @media screen and (max-width: 700px){
    height: 600px;
    background-image: url('../../../assets/images/minibanner-one.jpg');
    background-size: cover;
  }
  .inner{
    position: absolute;
    left: 50%;
    width: 100%;
    max-width: 1000px;
    height: 100%;
    transform: translateX(-50%);
    .banner-inner{
      position: absolute;
      top: 50%;
      width: 100%;
      transform: translateY(-50%);
      font-weight: 500;
      @media screen and (max-width: 700px){
        top: 20%;
        padding: 0 30px;
        text-align: center;
      }
      .banner-header{
        font-size: 20px;
      }
      .banner-body{
        font-size: $iconSize;
      }
      .banner-time{
        font-size: 18px;
        margin-top: 10px;
      }
      .banner-button{
        margin-top: 40px;
        font-size: $contentSize;
        display: inline-block;
        background: #eb0028;
        color: #fff;
        text-align: center;
        line-height: 50px;
        padding: 0 3rem;
        border-radius: 2px;
        position: relative;
        transform: translate(0%);
        overflow: hidden;
        box-sizing: border-box;
        @media screen and (max-width: 700px){
          margin-top: 20px;
          margin-bottom: 10px;
          height: 40px;
          font-size: 14px;
          line-height: 40px;
        }
        &:hover{
        &::before{
          content: "";
          display: block;
          position: absolute;
          top: -1px;
          left: -1px;
          width: calc(100% + 2px);
          height: calc(100% + 2px);
          display: block;
          z-index: -1;
          background: #b8001f;
          border-radius: 2px;
          animation: moveButton .25s ease forwards;
        }
        }
      }
    }
  }
}
.banner-two{
  background: url('../../../assets/images/banner-two.jpg') center center no-repeat;
  @media screen and (max-width: 700px){
    height: 600px;
    background-image: url('../../../assets/images/minibanner-two.jpg');
    background-size: cover;
  }
  .inner{
    .banner-inner{
      .banner-header{
        font-size: 40px;
        @media screen and (max-width: 700px){
          font-size: 28px;
        }
      }
      .banner-button{
        color: #000;
        background: transparent;
        border: 1px solid #101920;
        &:hover{
          color: #fff;
        &::before{
          background: #101920;
        }
        }
      }
    }
  }

}
.byron{
  opacity: 1;
  transform: scale(1);
}
</style>

<script>
export default {
  name: 'HomeBanner',
  data () {
    return {
      buttonTop: [],
      isByron: [false, false]
    }
  },
  methods: {
    getButtontop () {
      this.buttonTop[0] = Math.floor((this.$refs.offsetone.offsetTop) / 2)
      this.buttonTop[1] = Math.floor((this.$refs.offsettwo.offsetTop) / 2)
      // console.log(this.buttonTop)
    },
    getScroll () {
      // console.log(document.documentElement.scrollTop)
      for (let i = 0; i < this.buttonTop.length; i++) {
        if (this.buttonTop[i] < document.documentElement.scrollTop) {
          // 切记要使用set，否则不会渲染到页面，使用this.isByron[i]=true是无效的
          this.$set(this.isByron, i, true)
        } else {
          this.$set(this.isByron, i, false)
        }
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.getScroll)
    this.getButtontop()
  }

}
</script>
