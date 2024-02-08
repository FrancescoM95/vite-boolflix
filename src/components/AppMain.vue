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
        <div id="loader" v-if="!movies.length && !tvSeries.length">
            <h3>Film, serie Tv e nient'altro. <br>
                Senza limiti.
            </h3>
        </div>
        <div class="container" v-else>
            <section>
                <h2>Film</h2>
                <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 g-3">
                    <AppCard v-for="movie in movies" :key="movie.id" :production="movie" />
                </div>
            </section>

            <section>
                <h2>Serie Tv</h2>
                <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 g-3">
                    <AppCard v-for="tvSerie in tvSeries" :key="tvSerie.id" :production="tvSerie" />
                </div>
            </section>
        </div>


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
        margin: 30px 0;
    }
}

#loader {
    background-image: url('../assets/img/loader.png');
    background-size: cover;
    min-height: calc(100vh - 140px);
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;

    &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
    }

    h3 {
        font-size: 5rem;
        text-align: center;
        z-index: 1;
    }
}
</style>