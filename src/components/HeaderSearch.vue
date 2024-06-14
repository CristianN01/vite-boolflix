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
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=29f42ebaba6771b07ad5be78ceeaf393&query=' + this.store.searchFilm)
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
    },

}
</script>

<template>
   <input type="text" placeholder="Cerca un film" v-model="this.store.searchFilm">
   <button @click="getFilms()">cerca</button>
</template>

<style lang="scss" scoped>

</style>