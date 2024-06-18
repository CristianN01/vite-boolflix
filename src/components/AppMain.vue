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
    <article>
                        <!-- info -->
        <section class="film" v-for="film in store.films">
            <img :src="'https://image.tmdb.org/t/p/' + 'w342/' + film.poster_path" alt="">
            <h1>Titolo: <span>{{ film.title }}</span></h1>
            <h2>Titolo originale: <span>{{ film.original_title }}</span></h2>
            <h4>Lingua originale:
                <img class="lang-icon" :class="'lang-icon-' + film.original_language" src="" alt="">
            </h4>
            <h3>Voto: <span>{{ (Math.floor(film.vote_average / 2)) }}</span></h3>
        </section>
    
        <section class="tv-series" v-for="series in store.series">
            <img :src="'https://image.tmdb.org/t/p/' + 'w342/' + series.poster_path" alt="">
            <h1>Titolo: <span>{{ series.name}}</span></h1>
            <h2>Titolo originale: <span>{{ series.original_name }}</span></h2>
            <h4>Lingua originale:
                <img class="flag lang-icon" :class="'lang-icon-' + series.original_language" src="" alt="">
            </h4>
            <h3>Voto: <span>{{ (Math.floor(series.vote_average / 2)) }}</span></h3>
        </section> 
    </article>
    


</template>

<style lang="scss" scoped>
@use '../../node_modules/@textabledev/langs-flags-list/lang-flags.css' as *;

        .lang-icon {
            background-image: url(../../node_modules/@textabledev/langs-flags-list/lang-flags.png);
        }

        .flag{
            vertical-align: middle
        }

        article {
            display: flex;
            flex-wrap: wrap;
            background-color: #141414;

            .film {
                width: calc(100% / 5);
                margin-bottom: 3rem;
                color: white;

                h1 {
                    font-size: 1.5rem;
                }

                h2 {
                    font-size: 1rem;
                }
            }
        }
    

    .tv-series {
        margin-top: 3rem;
    }

    // .lang-icon {
    // background-image: url(../lang-flags.png);
    // }
</style>