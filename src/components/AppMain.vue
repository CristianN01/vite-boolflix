<script>
import { store } from "../store.js";

export default {
  data() {
    return {
        store,
      
    }
  },
  methods: {
        starsVote(){
            return Math.ceil(store.film.vote_average / 2)
        }
    }
}
</script>

<template>
    <article>
                        <!-- info -->
        <section class="film" v-for="film in store.films">
            <img  v-if="film.poster_path != null" class="image-poster" :src="'https://image.tmdb.org/t/p/' + 'w342/' + film.poster_path" alt="">
            <img  v-else class="image-poster placeholder" src="../img/vertical-placeholder-image.jpg" alt="placeholder">
            <div class="info-block">
                <h1>Titolo: <span>{{ film.title }}</span></h1>
                <h2>Titolo originale: <span>{{ film.original_title }}</span></h2>
                <h4>Lingua originale:
                    <img class="lang-icon" :class="'lang-icon-' + film.original_language" src="" alt="">
                </h4>
                <h3>Voto: <span>{{ (Math.floor(film.vote_average / 2)) }}</span></h3>
            </div>
        </section>

    
        <section class="tv-series" v-for="series in store.series">
            <img  v-if="series.poster_path != null" class="image-poster" :src="'https://image.tmdb.org/t/p/' + 'w342/' + series.poster_path" alt="">
            <img  v-else class="image-poster placeholder" src="../img/vertical-placeholder-image.jpg" alt="placeholder">
            <div class="info-block">
                <h1>Titolo: <span>{{ series.name}}</span></h1>
                <h2>Titolo originale: <span>{{ series.original_name }}</span></h2>
                <h4>Lingua originale:
                    <img class="flag lang-icon" :class="'lang-icon-' + series.original_language" src="" alt="">
                </h4>
                <h3>Voto: <span>{{ (Math.floor(series.vote_average / 2)) }}</span></h3>
            </div>
        </section> 
    </article>

    


</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
@use '../../node_modules/@textabledev/langs-flags-list/lang-flags.css' as *;
@use '../../node_modules/@fortawesome/fontawesome-free/css/all.css' as *;

        .lang-icon {
            background-image: url(../../node_modules/@textabledev/langs-flags-list/lang-flags.png);
        }

        .flag{
            vertical-align: middle
        }

        .placeholder {
            width: 95%;
        }

        article {
            display: flex;
            flex-wrap: wrap;
            background-color: #141414;

            .film,
            .tv-series {
                width: calc((100% / 5) - 1rem);
                margin-bottom: 3rem;
                color: white;
                height: 500px;
                margin-left: 1rem;
                margin-top: 1rem;

                h1 {
                    font-size: 1.5rem;
                }

                h2 {
                    font-size: 1rem;
                }
            }
        }

        .info-block {
            display: none;
        }

    .film,
    .tv-series {
    
        position: relative;

        &:hover {
                .image-poster {
                    filter:opacity(20%);
                    
                    
                }

                .info-block {
                    display: inline;
                    position: relative;
                    bottom: 450px;
                    
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