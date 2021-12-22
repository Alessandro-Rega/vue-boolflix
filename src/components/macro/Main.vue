<template>
  <main>
      <Search @cercaFilm="searchMovie" />
      <div class="contenitore">
        <Film v-for="(film, index) in arrayFilm" :key="index" :film="film"/>
        <Series v-for="(series, index) in arraySeries" :key="index" :series="series"/>
      </div>
  </main>
</template>

<script>
import Search from '../sections/Search'
import Film from '../sections/Film'
import Series from '../sections/Series'

import axios from "axios"

export default {
    name: 'Main',
    components: {
        Search,
        Film,
        Series,
    },
    data(){
        return{
            arrayFilm: [],
            arraySeries: [],
        }
    },
    methods:{
        searchMovie(cerca, selezione_film){
            if(selezione_film == true){
                this.arraySeries = [];
                this.arrayFilm = [];
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
                    this.stelline(selezione_film);
                    console.log(response.data.results);
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
            }
            else{
                this.arrayFilm = [];
                this.arraySeries = [];
                axios
                .get("https://api.themoviedb.org/3/search/tv", {
                    params: {
                    api_key: "aa336647215e508c9724202ef49eaffc",
                    query: cerca,
                    language: "it-IT",
                    },
                })
                .then((response) => {
                    this.arraySeries = response.data.results;
                    this.stelline(selezione_film);
                    console.log(response.data.results);
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
            }
        },
        stelline(selezione_film){
            if(selezione_film == true){
                for(let i = 0; i < this.arrayFilm.length; i++){
                    this.arrayFilm[i].vote_average /= 2;
                    const int_part = Math.trunc(this.arrayFilm[i].vote_average);
                    const float_part = Number((this.arrayFilm[i].vote_average-int_part).toFixed(2));
                    if(float_part >= 0.5)this.arrayFilm[i].vote_average = parseInt(this.arrayFilm[i].vote_average) + 1;
                    else this.arrayFilm[i].vote_average = parseInt(this.arrayFilm[i].vote_average);
                }
            }
            else {
               for(let i = 0; i < this.arraySeries.length; i++){
                    this.arraySeries[i].vote_average /= 2;
                    const int_part = Math.trunc(this.arraySeries[i].vote_average);
                    const float_part = Number((this.arraySeries[i].vote_average-int_part).toFixed(2));
                    if(float_part >= 0.5)this.arraySeries[i].vote_average = parseInt(this.arraySeries[i].vote_average) + 1;
                    else this.arraySeries[i].vote_average = parseInt(this.arraySeries[i].vote_average);
                } 
            }
        }
    }
}
</script>

<style scoped lang="scss">

.contenitore{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 20px 10px;
}

</style>