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
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@300;700&display=swap');

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body{
  background-color: #222222;
  font-family: 'Oswald', sans-serif;
}
</style>
