<script>
import AppCard from '../AppCard.vue';
import { store } from '../components/data/store';
export default {
    name: 'AppMain',
    data: () => ({

    }),
    components: { AppCard },
    computed: {
        movies() {
            return store.movies;
        },
        tvSeries() {
            return store.tvSeries;
        }
    }

}
</script>

<template>
    <main>
        <section class="container">
            <h2>Film</h2>
            <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 g-2">
                <AppCard v-for="movie in movies" :key="movie.id" :production="movie" />
            </div>
        </section>

        <section class="container">
            <h2>Serie Tv</h2>
            <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4">
                <AppCard v-for="tvSerie in tvSeries" :key="tvSerie.id" :production="tvSerie" />
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
</style>