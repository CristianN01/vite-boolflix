<script>
import { store } from "../store.js";
import axios from 'axios'

export default {
  data() {
    return {
        store,
      
    }
  },
  methods: {
      getFilms(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=29f42ebaba6771b07ad5be78ceeaf393&query=' + this.store.search)
            .then( (response) => {
                // handle success
                console.log(response.data.results);
                this.store.films = response.data.results;
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .finally(function () {
                // always executed
            });
        },

        getTvSeries(){
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=' + this.store.search)
            .then( (response) => {
                // handle success
                console.log(response.data.results);
                 this.store.series = response.data.results;
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .finally(function () {
                // always executed
            });
        }
    },

}
</script>

<template>
    <section class="nav">
        <div class="boolflix">
            <img class="profile" src="../../src/img/netflix-profile-pictures-1000-x-1000-qo9h82134t9nv0j0.jpg" alt="">
            <h1>
                BOOLFLIX
            </h1>
        </div>
        <div class="search">
            <input type="text" placeholder="Cerca un film/Serie" v-model="this.store.search" >
            <button @click="getFilms() + getTvSeries()">cerca</button>
        </div>
    </section>
</template>



<style lang="scss" scoped>

.boolflix {
    display: flex;
    margin: 0;
    justify-content: baseline;

    img,
    h1 {
        margin: 0;
        align-self: center;
        color: #e50914;
        font-size: 30px;
        margin-left: 2rem;
    }
}

.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .profile {
        width: 5%;
        border-radius: 10px;
        justify-content: center;
    }
}

.search {

    input {
        border-radius: 10px;
        border-color: #e50914;
        margin-right: 2rem;
        width: 20rem;
        padding: 0.25rem;
        background-color: rgba(0, 0, 0, 0.292);
        color: white;
    }

    button {
        border-radius: 10px;
        padding: 0.25rem 1rem;
        color: white;
        background-color: #141414;
        border-color: #e50914;
    }
}

</style>