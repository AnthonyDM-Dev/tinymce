<template>
  <div class="hello" :class="classes">
    <h1>{{ msg }}<br>{{ msg2 }}<br> {{ msg3 }}<br></h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    msg2: String,
    msg3: String,
    classes: String
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/hello-world.scss';
</style>
