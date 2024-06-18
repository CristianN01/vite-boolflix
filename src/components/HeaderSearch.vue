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
        <h1>
            BOOLFLIX
        </h1>
        <div class="search">
            <input type="text" placeholder="Cerca un film/Serie" v-model="this.store.search" >
            <button @click="getFilms() + getTvSeries()">cerca</button>
        </div>
    </section>
</template>



<style lang="scss" scoped>

.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1 {
        color: red;
        font-size: 30px;
    }
}

</style>