<template>
  <div class="all">
    <div class="contain">
      <ul>
        <li>
          <i class="iconfont">&#xe603;</i>
          <span>OnePlus 7T</span>
        </li>
        <li>
          <i class="iconfont">&#xe603;</i>
          <span>OnePlus 7T Pro</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '../assets/style/scss/custom.scss';

.all{
  position: absolute;
  width: 100%;
  height: 160px;
  background: #fff;
  box-shadow: 0 4px 10px rgba(0,0,0,.1);
  border-top: 1px solid #666;
  z-index: 999;
  .contain{
    max-width: 1200px;
    height: 160px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
    ul{
      list-style: none;
      display: flex;
      flex-wrap: nowrap;
      li{
        max-height: 120px;
        padding: 10px 30px 0;
        margin-top: 20px;
        text-align: center;
        font-weight: 600;
        i{
          display: block;
          margin-bottom: 10px;
          font-size: $iconSize;
        }
      }
    }
  }
}
</style>

<script>
export default {
  name: 'Version'
}
</script>
