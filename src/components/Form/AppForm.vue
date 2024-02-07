<script>
import axios from 'axios';
import FormImput from './FormImput.vue';
export default {
    name: 'AppForm',
    data: () => ({
        currentValue: '',
        baseUriMovie: 'https://api.themoviedb.org/3/search/movie?query=',
        api_keys: '&language=it-IT&api_key=affd5dce05723e00eba8a879024625c8',
        movies: [],

    }),
    components: { FormImput },
    methods: {
        readValue(searchText) {
            this.currentValue = searchText
        },
        sendForm() {
            axios.get(this.currentURL).then(res => {
                this.movies = res.data.results;
                console.log(this.filteredMovies)
            })
        }
    },
    computed: {
        currentURL() {
            return this.baseUriMovie + this.currentValue + this.api_keys
        },
        filteredMovies() {
            return this.movies.map(movie => {
                return {
                    "title": movie.title,
                    "original title": movie.original_title,
                    "language": movie.original_language,
                    "vote": movie.vote_average
                };
            })
        }
    }
}
</script>

<template>
    <form @submit.prevent="sendForm">
        <FormImput @value-change="readValue" />
        <button>Cerca</button>
    </form>
</template>
  
<style lang="scss"></style>