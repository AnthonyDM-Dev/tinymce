<template>
  <div id="app">
    <AppHeader :links="links" />
    <router-view/>
  </div>
</template>
<script>
import AppHeader from './components/AppHeader.vue'
export default {
  components: {
    AppHeader
  },
  data () {
    return {
      links: [
        { label: 'Home', link: '/' },
        { label: 'Editor', link: '/editor' }
      ]
    }
  }
}
</script>
<style lang="scss" scoped>
@import './assets/styles/app.scss';
</style>
