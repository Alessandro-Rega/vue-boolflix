<template>
  <div class="header">
      <img src="../../assets/img/Netflix-Logo.png" alt="logo">

    <div class="search">
      <div class="select">
          <span @click="selezione_film = true, $emit('cercaFilm', cerca, selezione_film)" :class="selezione_film == true ? 'selezionato' : ''">Film</span>
          <span @click="selezione_film = false, $emit('cercaFilm', cerca, selezione_film)" :class="selezione_film == true ? '' : 'selezionato'">Serie TV</span>
      </div>
      <div class="input_search">
        <input type="text" v-model="cerca" v-on:keyup.enter="$emit('cercaFilm', cerca, selezione_film)">
        <button class="btn" @click="$emit('cercaFilm', cerca, selezione_film)"><i class="fas fa-search"></i></button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Search',
    data(){
        return{
            cerca: "",
            selezione_film: true,
        }
    }
}
</script>

<style lang="scss" scoped>

.header{
    display: flex;
    align-items: center;
    height: 100px;
    background-color: #1b1b1b;

    img[alt="logo"]{
    height: 80px;
    margin: 0 30px;
    }
    
        .search{
            display: flex;
            justify-content: space-between;
            width: 100%;
            margin: 0 30px;

            .select{
                display: flex;
                align-items: center;
            }

            span{
                color: rgb(168, 168, 168);
                margin-right: 20px;
                cursor: pointer;
            }

            span.selezionato{
                position: relative;
                color: white;
            }

            span.selezionato::after{
                content: "";
                position: absolute;
                width: 100%;
                height: 2.5px;
                bottom: -38px;
                left: 0;
                color: white;
                background-color: white;
            }

            .input_search{
                display: flex;
                align-items: center;
                .btn{
                    margin: 0 5px;
                    padding: 5px 7px;
                    font-size: 18px;
                    border: none;
                    color: white;
                    background-color: #1b1b1b;
                    cursor: pointer;
                }
            }
        }
}

</style>