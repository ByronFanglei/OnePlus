<template>
  <div>
    <home-header></home-header>
    <home-content></home-content>
    <home-banner></home-banner>
  </div>
</template>

<script>
import HomeHeader from './conponents/Header'
import HomeContent from './conponents/content'
import HomeBanner from './conponents/banner'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeContent,
    HomeBanner
  }
}
</script>
