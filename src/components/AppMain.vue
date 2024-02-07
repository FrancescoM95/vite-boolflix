<script>
import { store } from '../components/data/store';
export default {
    name: 'AppMain',
    data: () => ({

    }),
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
                <p>Lingua: {{ movie.original_language }}</p>
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
</style>