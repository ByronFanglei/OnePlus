<template>
  <div class="all">
    <b-container>
      <b-row class="contain">
        <b-col class="contain-col" lg="2">
          <div>
            <div class="contain-col-icon">
              <span class="iconfont">&#xe603;</span>
            </div>
            <p>OnePlus 7T</p>
          </div>
        </b-col>
        <b-col class="contain-col" lg="2">
          <div>
            <div class="contain-col-icon">
              <span class="iconfont">&#xe603;</span>
            </div>
            <p>OnePlus 7T</p>
          </div>
        </b-col>
    </b-row>
    </b-container>
  </div>
</template>

<style lang="scss" scoped>
@import '../assets/style/scss/custom.scss';

.all{
  widows: 100%;
  height: 160px;
  background: #fff;
  box-shadow: 0 4px 10px rgba(0,0,0,.1);
  border-top: 1px solid #666;
  .contain{
    justify-content: center;
    align-items: center;
    .contain-col{
      margin-top: 20px;
      padding: 10px 10px 0;
      text-align: center;
      color: #101920;
      font-weight: 600;
      .contain-col-icon{
        margin-bottom: 20px;
        span{
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
