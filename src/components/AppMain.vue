<script>
import { store } from '../components/data/store';
export default {
    name: 'AppMain',
    data: () => ({

    }),
    methods: {
        getLangFlag(lang) {
            if (lang === 'it' || lang === 'en') {
                return ('../../src/assets/img/' + lang + '.png');
            } else {
                return '';
            }
        }
    },
    computed: {
        movies() {
            return store.movies
        }
    }
}
</script>

<template>
    <main>
        <section class="container">
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
    </main>
</template>
  
<style lang="scss">
main {
    color: #fff;
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