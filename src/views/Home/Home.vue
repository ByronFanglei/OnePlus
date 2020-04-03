<template>
  <div>
    <home-header></home-header>
    <home-content></home-content>
    <home-banner></home-banner>
    <home-four></home-four>
    <home-shot></home-shot>
    <home-promos></home-promos>
  </div>
</template>

<script>
import HomeHeader from './conponents/Header'
import HomeContent from './conponents/Content'
import HomeBanner from './conponents/Banner'
import HomeFour from './conponents/Four'
import HomeShot from './conponents/Shot'
import HomePromos from './conponents/Promos'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeContent,
    HomeBanner,
    HomeFour,
    HomeShot,
    HomePromos
  }
}
</script>
