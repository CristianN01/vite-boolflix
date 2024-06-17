<script>
import { store } from "../store.js";

export default {
  data() {
    return {
        store,
      
    }
  }
}
</script>

<template>
    <section class="film">
        <ul>
            <li v-for="film in store.films">
                <h1>Films</h1>
                Titolo :{{ film.title }}
                Titolo originale :{{ film.original_title }}
                Lingua :{{ film.original_language }}
                Voto :{{ film.vote_count }}
            </li>
        </ul>
    </section>
    <section class="tv-series">
        <ul>
            <li v-for="series in store.series">
                <h1>Tv-Series</h1>
                Titolo: {{ series.name }}
                Titolo originale: {{ series.original_name }}
                Lingua: {{ series.original_language }}
                Voto: {{ series.vote_average }}
            </li>
        </ul>
    </section>
</template>

<style lang="scss" scoped>

        li {
            border: 2px solid black;
            margin-top: 1rem;
            list-style-type: none;
        }
    

    .tv-series {
        margin-top: 3rem;
    }
</style>