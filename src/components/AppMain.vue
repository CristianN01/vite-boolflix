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
                Titolo :{{ film.title }}
                Titolo originale :{{ film.original_title }}
                Lingua :{{ film.original_language }}
                Voto :{{ film.vote_count }}
            </li>
        </ul>
    </section>
</template>

<style lang="scss" scoped>

</style>