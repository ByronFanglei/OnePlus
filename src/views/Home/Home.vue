<template>
  <div>
    <home-header></home-header>
    <home-content></home-content>
  </div>
</template>

<script>
import HomeHeader from './conponents/Header'
import HomeContent from './conponents/content'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeContent
  }
}
</script>
