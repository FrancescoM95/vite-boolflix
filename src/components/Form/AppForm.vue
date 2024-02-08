<script>
import axios from 'axios';
import { store } from '../data/store'
import FormImput from '../Form/FormImput.vue'
export default {
    name: 'AppForm',
    data: () => ({
        currentValue: '',
        baseUriMovie: 'https://api.themoviedb.org/3/search/movie?query=',
        baseUriTv: 'https://api.themoviedb.org/3/search/tv?query=',
        api_keys: '&language=it-IT&api_key=affd5dce05723e00eba8a879024625c8',
    }),
    components: { FormImput },
    methods: {
        readValue(searchText) {
            this.currentValue = searchText
        },
        sendForm() {
            axios.get(this.currentURLMovie).then(res => {
                store.movies = res.data.results;
                console.log(this.filteredMovies)
            });
            axios.get(this.currentURLTv).then(res => {
                store.tvSeries = res.data.results;
                console.log(this.filteredTvSeries)
            });

        }
    },
    computed: {
        currentURLMovie() {
            return this.baseUriMovie + this.currentValue + this.api_keys
        },
        currentURLTv() {
            return this.baseUriTv + this.currentValue + this.api_keys
        },
        filteredMovies() {
            return store.movies.map(movie => {
                return {
                    "title": movie.title,
                    "original title": movie.original_title,
                    "language": movie.original_language,
                    "vote": movie.vote_average,
                    "poster_path": movie.poster_path,
                    "overview": movie.overview
                };
            })
        },
        filteredTvSeries() {
            return store.tvSeries.map(tvSerie => {
                return {
                    "title": tvSerie.name,
                    "original title": tvSerie.original_name,
                    "language": tvSerie.original_language,
                    "vote": tvSerie.vote_average,
                    "poster_path": tvSerie.poster_path,
                    "overview": tvSerie.overview
                };
            })
        }
    }
}
</script>

<template>
    <form @submit.prevent="sendForm" class="d-flex gap-3 w-50">
        <FormImput @value-change="readValue" />
        <button class="btn btn-outline-danger button">Cerca</button>
    </form>
</template>
  
<style lang="scss">
.button {
    background-color: #D40000;
    color: #fff;
}
</style>