<template>
  <div class="film_card">
      <img :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="">
      <span>{{film.title}}</span>
      <span>{{film.original_title}}</span>
      <span>{{film.original_language}}</span>
      <span>{{film.vote_average}}</span>
  </div>
</template>

<script>
export default {
    name: 'Film',
    props:{
        film: Object,
    }
}
</script>

<style lang="scss" scoped>
span{
    display: block;
}
</style>