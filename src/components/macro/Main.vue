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
                },
            })
            .then((response) => {
                this.arrayFilm = response.data.results;
                this.stelline();
                console.log(response.data.results);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });
        },
        stelline(){
            for(let i = 0; i < this.arrayFilm.length; i++){
                this.arrayFilm[i].vote_average /= 2;
                const int_part = Math.trunc(this.arrayFilm[i].vote_average);
                const float_part = Number((this.arrayFilm[i].vote_average-int_part).toFixed(2));
                if(float_part >= 0.5)this.arrayFilm[i].vote_average = parseInt(this.arrayFilm[i].vote_average) + 1;
                else this.arrayFilm[i].vote_average = parseInt(this.arrayFilm[i].vote_average);
            }
        }
    }
}
</script>

<style scoped lang="scss">

</style>