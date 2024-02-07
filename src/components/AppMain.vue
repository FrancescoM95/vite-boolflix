<script>
import { store } from '../components/data/store';
export default {
    name: 'AppMain',
    data: () => ({

    }),
    methods: {
        getLangFlag(lang) {
            return (lang === 'it' || lang === 'en') ? ('../../src/assets/img/' + lang + '.png') : '';
        }
    },
    computed: {
        movies() {
            return store.movies
        },
        tvSeries() {
            return store.tvSeries
        }
    }
}
</script>

<template>
    <main>
        <section class="container">
            <h2>Film</h2>
            <div v-for="movie in movies" :key="movie.title">
                <h3>{{ movie.title }}</h3>
                <p>Titolo Originale: {{ movie.original_title }}</p>
                <div id="language">
                    <p>Lingua:</p>
                    <p v-if="!getLangFlag(movie.original_language)">{{ movie.original_language }}</p>
                    <img v-else :src="getLangFlag(movie.original_language)" :alt="movie.original_language">
                </div>
                <p>Voto: {{ movie.vote_average }}</p>
                <hr>
            </div>
        </section>

        <section class="container">
            <h2>Serie Tv</h2>
            <div v-for="tvSerie in tvSeries" :key="tvSerie.name">
                <h3>{{ tvSerie.name }}</h3>
                <p>Titolo Originale: {{ tvSerie.original_name }}</p>
                <div id="language">
                    <p>Lingua:</p>
                    <p v-if="!getLangFlag(tvSerie.original_language)">{{ tvSerie.original_language }}</p>
                    <img v-else :src="getLangFlag(tvSerie.original_language)" :alt="tvSerie.original_language">
                </div>
                <p>Voto: {{ tvSerie.vote_average }}</p>
                <hr>
            </div>
        </section>


    </main>
</template>
  
<style lang="scss">
main {
    color: #fff;

    h2 {
        color: #D40000;
        text-align: center;
        text-transform: uppercase;
        font-size: 2.5rem;
    }
}

#language {
    display: flex;
    align-items: center;
    gap: 10px;

    img {
        width: 25px;
        height: 15px;
        margin-bottom: 16px;
    }
}
</style>