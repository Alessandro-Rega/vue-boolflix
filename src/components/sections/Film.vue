<template>
  <div class="film_card">

        <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="poster" class="post">
        <img v-else src="../../assets/img/not-found.png" alt="poster" class="post">

        <div class="container">
            <div class="titolo">
                <span>Titolo: </span>
                <span>{{film.title}}</span>
            </div>

            <div class="titolo_originale">
                <span>Titolo originale: </span>
                <span>{{film.original_title}}</span>
            </div>

            <div class="bandiera">
                <img v-if="film.original_language == ('it' || 'en' || 'es' || 'fr' || 'gr' || 'zh')" :src="require('../../assets/flags/' + film.original_language + '.png')" :alt="film.original_language">
                <img v-else src="" alt="404">
            </div>


            <div class="voto">
                <i class="fas fa-star" :class=" film.vote_average > 0 ? 'stella_on' : '' "></i>
                <i class="fas fa-star" :class=" film.vote_average > 1 ? 'stella_on' : '' "></i>
                <i class="fas fa-star" :class=" film.vote_average > 2 ? 'stella_on' : '' "></i>
                <i class="fas fa-star" :class=" film.vote_average > 3 ? 'stella_on' : '' "></i>
                <i class="fas fa-star" :class=" film.vote_average > 4 ? 'stella_on' : '' "></i>
            </div>

            <div class="descrizione">
                <p>{{film.overview}}</p>
            </div>
        </div>

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

.voto{
    .stella_on{
        color: #ffbd00;
    }
}

.film_card{
    width: max-content;
    height: max-content;
    position: relative;
    margin: 0 10px;
    margin-bottom: 30px;

    .post{
        width: 342px;
        height: 513px;
    }

    &:hover .container{
        opacity: 1;
        transition: 0.7s;
    }

    .container{
        opacity: 0;
        width: 342px;
        height: 513px;
        position: absolute;
        top: 0;
        left: 0;
        padding: 10px;
        padding-top: 50px;
        background-color: rgba(0,0,0,0.7);
        color: white;
        transition: 0.7s;
        cursor: pointer;

        .titolo, .titolo_originale{
            span:first-child{
                font-weight: bold;
            }
        }

        .bandiera{
            display: flex;
            align-items: center;
            img{
            width: 20px;
            }
            &::before{
                content: "Lingua: ";
                margin-right: 5px;
                font-weight: bold;
            }
        }
        
    }
}

</style>