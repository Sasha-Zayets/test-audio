<template>
  <div id="app">
    <widgets></widgets>
  </div>
</template>
<script>
import widgets from './views/widgets'
export default {
  components: {
    widgets
  }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto');
body {
  font-family: 'Roboto', sans-serif;
}
</style>
