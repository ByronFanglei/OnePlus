<template>
  <div class="shotall">
    <div class="shot" ref="offset" :class="{byron: isByron}">
      <div class="shot-font">
        <div class="font-one">Shot on OnePlus</div>
        <div class="font-two">我要参加</div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '../../../assets/style/scss/custom.scss';
@import '../../../assets/style/scss/animation.scss';
.shotall{
  overflow: hidden;
  width: 100%;
  height: 720px;
  @media screen and (max-width: 700px){
    height: 50vw;
  }
}
.shot{
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: url('../../../assets/images/shotone.jpg') center center no-repeat;
  background-size: cover;
  transform: scale(1.02);
  transition: all 1s cubic-bezier(0.25,0.1, 0.25 ,1);
  .shot-font{
    width: 100%;
    text-align: center;
    color: #fff;
    .font-one{
      font-size: 48px;
      margin-bottom: 40px;
      @media screen and (max-width: 700px){
        font-size: 26px;
      }
    }
    .font-two{
      font-size: $contentSize;
      border: 1px solid #fff;
      display: inline-block;
      background: transparent;
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
        font-size: 12px;
        line-height: 30px;
        padding: 0 1rem;
      }
      &:hover{
        color: #000;
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
        background: #fff;
        border-radius: 2px;
        animation: moveButton .5s ease forwards;
      }
      }
    }
  }
}
.byron{
  transform: scale(1);
}
</style>

<script>
export default {
  name: 'HomeShot',
  data () {
    return {
      offset: 0,
      isByron: false
    }
  },
  methods: {
    getOffset () {
      this.offset = Math.floor(this.$refs.offset.offsetTop / 1.8)
    },
    getScroll () {
      if (this.offset < document.documentElement.scrollTop) {
        this.isByron = true
      } else {
        this.isByron = false
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.getScroll)
    this.getOffset()
  }
}
</script>
