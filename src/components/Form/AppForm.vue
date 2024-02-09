<script>
import axios from 'axios';
import { store } from '../data/store'
import FormInput from '../Form/FormInput.vue'
export default {
    name: 'AppForm',
    data: () => ({
        currentValue: '',
        baseUriMovie: 'https://api.themoviedb.org/3/search/movie',
        baseUriTv: 'https://api.themoviedb.org/3/search/tv',
        apiKey: 'affd5dce05723e00eba8a879024625c8'
    }),
    components: { FormInput },
    methods: {
        readValue(searchText) {
            this.currentValue = searchText
        },
        sendForm() {
            axios.get(this.currentURLMovie)
                .then(movieResponse => {
                    store.movies = movieResponse.data.results;
                    console.log('Movies:', this.filteredMovies);
                })
                .catch(error => {
                    console.error('Err:', error);
                });

            axios.get(this.currentURLTv)
                .then(tvResponse => {
                    store.tvSeries = tvResponse.data.results;
                    console.log('TV Series:', this.filteredTvSeries);
                })
                .catch(error => {
                    console.error('Err:', error);
                });
        }
    },
    computed: {
        currentURLMovie() {
            return `${this.baseUriMovie}?query=${this.currentValue}&language=it-IT&api_key=${this.apiKey}`;
        },
        currentURLTv() {
            return `${this.baseUriTv}?query=${this.currentValue}&language=it-IT&api_key=${this.apiKey}`;
        },
        filteredMovies() {
            return store.movies.map(movie => {
                return {
                    id: movie.id,
                    title: movie.title,
                    originalTitle: movie.original_title,
                    language: movie.original_language,
                    vote: movie.vote_average,
                    posterPath: movie.poster_path,
                    overview: movie.overview,
                };
            })
        },
        filteredTvSeries() {
            return store.tvSeries.map(tvSerie => {
                return {
                    id: tvSerie.id,
                    title: tvSerie.name,
                    originalTitle: tvSerie.original_name,
                    language: tvSerie.original_language,
                    vote: tvSerie.vote_average,
                    posterPath: tvSerie.poster_path,
                    overview: tvSerie.overview,
                };
            })
        }
    }
}
</script>

<template>
    <form @submit.prevent="sendForm" class="d-flex gap-3 w-50">
        <FormInput @value-change="readValue" />
        <button type="submit" class="btn btn-outline-danger button">Cerca</button>
    </form>
</template>
  
<style lang="scss">
.button {
    background-color: #D40000;
    color: #fff;
}
</style>