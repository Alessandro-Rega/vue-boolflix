<template>
  <div class="search">
      <input type="text" v-model="cerca">
      <button class="btn" @click="$emit('cercaFilm', cerca)">Cerca</button>
  </div>
</template>

<script>

export default {
    name: 'Search',
    data(){
        return{
            cerca: ""
        }
    }
}
</script>

<style lang="scss" scoped>

</style>