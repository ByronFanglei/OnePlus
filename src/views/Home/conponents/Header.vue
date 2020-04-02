<template>
  <div class="header">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand iconfont" href="#" id="logo">&#xe830;</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
      </div>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav" id="byron-center">
          <li class="nav-item" id="byron-one">
            <a class="nav-link" href="#" @mouseenter="enter" @mouseleave="leave">7T系列</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">商场</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">品牌</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">服务</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">论坛</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">零售店</a>
          </li>
        </ul>
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown right>
            <template v-slot:button-content>
              <em class="iconfont">&#xe602;</em>
            </template>
            <b-dropdown-item href="#" class="border-bottom">订单</b-dropdown-item>
            <b-dropdown-item href="#" class="border-bottom">账户</b-dropdown-item>
            <b-dropdown-item href="#" class="border-bottom">推荐有礼</b-dropdown-item>
            <b-dropdown-item href="#">登录</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item-dropdown right id="byron-shopping">
            <template v-slot:button-content>
              <em class="iconfont">&#xe65a;</em>
            </template>
            <div class="d-block text-center border-bottom">
              <h6>Hello From This Modal!</h6>
            </div>
            <b-button class="mt-3" variant="danger" block @click="$bvModal.hide('bv-modal-example')">去购物</b-button>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </div>
    </nav>
    <version v-if="version"></version>
  </div>
</template>

<style lang="scss" scoped>
@import '../../../assets/style/scss/custom.scss';

.header{
  position: relative;
}
#byron-center{
  li{
    padding-right: 20px;
    a{
      color: #000;
      font-size: 14px;
    }
  }
}
.iconfont{
  font-size: $iconSize;
}
#logo{
    color: red;
}
</style>>

<script>
import Version from '../../../components/Version'
export default {
  name: 'HomeHeader',
  data () {
    return {
      version: false
    }
  },
  components: {
    Version
  },
  methods: {
    enter: function () {
      this.version = true
    },
    leave: function () {
      this.version = false
    }
  }
}
</script>
