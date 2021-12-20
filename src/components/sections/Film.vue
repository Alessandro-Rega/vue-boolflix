<template>
  <div class="film_card">
      <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="poster">
      <span>{{film.title}}</span>
      <span>{{film.original_title}}</span>
      <img v-if="film.original_language == 'it'" src="../../assets/flags/italy.png" alt="lingua">
      <img v-if="film.original_language == 'en'" src="../../assets/flags/uk.png" alt="lingua">
      <img v-if="film.original_language == 'es'" src="../../assets/flags/spain.png" alt="lingua">
      <img v-if="film.original_language == 'fr'" src="../../assets/flags/france.png" alt="lingua">
      <img v-if="film.original_language == 'gr'" src="../../assets/flags/germany.png" alt="lingua">
      <img v-if="film.original_language == 'zh'" src="../../assets/flags/japan.png" alt="lingua">
      <span>{{film.vote_average}}</span>
  </div>
</template>

<script>
export default {
    name: 'Film',
    props:{
        film: Object,
    },
}
</script>

<style lang="scss" scoped>
span{
    display: block;
}
</style>