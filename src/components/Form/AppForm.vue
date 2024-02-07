<script>
import axios from 'axios';
import { store } from '../data/store'
import FormImput from '../Form/FormImput.vue'
export default {
    name: 'AppForm',
    data: () => ({
        currentValue: '',
        baseUriMovie: 'https://api.themoviedb.org/3/search/movie?query=',
        api_keys: '&language=it-IT&api_key=affd5dce05723e00eba8a879024625c8',
    }),
    components: { FormImput },
    methods: {
        readValue(searchText) {
            this.currentValue = searchText
        },
        sendForm() {
            axios.get(this.currentURL).then(res => {
                store.movies = res.data.results;
                console.log(this.filteredMovies)
            })
        }
    },
    computed: {
        currentURL() {
            return this.baseUriMovie + this.currentValue + this.api_keys
        },
        filteredMovies() {
            return store.movies.map(movie => {
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
    <form @submit.prevent="sendForm" class="d-flex gap-3 my-3">
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