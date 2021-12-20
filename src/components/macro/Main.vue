<template>
  <main>
      <Search @cercaFilm="searchFilm" />
      <Film v-for="(film, index) in arrayFilm" :key="index" :film="film"/>
  </main>
</template>

<script>
import Search from '../sections/Search'
import Film from '../sections/Film'

import axios from "axios"

export default {
    name: 'Main',
    components: {
        Search,
        Film,
    },
    data(){
        return{
            arrayFilm: [],
        }
    },
    methods:{
        searchFilm(cerca){
            axios
            .get("https://api.themoviedb.org/3/search/movie", {
                params: {
                api_key: "aa336647215e508c9724202ef49eaffc",
                query: cerca,
                language: "it-IT",
                },
            })
            .then((response) => {
                this.arrayFilm = response.data.results;
                console.log(response.data.results);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });
        }
    }
}
</script>

<style scoped lang="scss">

</style>