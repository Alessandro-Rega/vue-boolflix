<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from "./components/macro/Main"

export default {
  name: 'App',
  components: {
    Main,
  }
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
