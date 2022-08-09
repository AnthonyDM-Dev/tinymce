<template>
  <div class="header">
    <nav>
      <router-link
        v-for="(link, i) in links"
        :key="i"
        :to="link.link"><p>{{ link.label }}</p></router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'AppHeader',
  props: {
    links: Array,
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/header.scss';
</style>
