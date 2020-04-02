<template>
  <div>
    <home-header></home-header>
    <home-content></home-content>
    <home-banner></home-banner>
    <home-four></home-four>
  </div>
</template>

<script>
import HomeHeader from './conponents/Header'
import HomeContent from './conponents/Content'
import HomeBanner from './conponents/Banner'
import HomeFour from './conponents/Four'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeContent,
    HomeBanner,
    HomeFour
  }
}
</script>
