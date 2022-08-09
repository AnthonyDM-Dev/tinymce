<template>
  <div id="home">
    <div class="home__heading-container">
      <HelloWorld
        msg="Welcome to my"
        msg2="tiny MCE"
        msg3="Editor"
        classes="slide-left"/>
      <div class="home__heading-image">
        <img class="home__logo" src="../assets/logo.png" />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/home.scss'
</style>