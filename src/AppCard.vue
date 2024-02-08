<script>
export default {
    name: 'AppCard',
    props: {
        production: Object
    },
    data() {
        return {
            showDetails: false,
            langs: ['it', 'en', 'es', 'fr', 'ja', 'ru', 'de', 'zh', 'ko']
        }
    },
    methods: {
        getLangFlag(lang) {
            return this.langs.includes(lang) ? ('../../src/assets/img/' + lang + '.png') : '';
        },
        getImageUrl(posterPath) {
            return posterPath ? `https://image.tmdb.org/t/p/w342${posterPath}` : 'https://via.placeholder.com/342x513?text=No+Image';
        }
    },
    computed: {
        starsCount() {
            return Math.ceil(this.production.vote_average / 2);
        },
        voteAverage() {
            return Math.floor(this.production.vote_average);
        }
    }
}
</script>

<template>
    <div class="col text-center">
        <div class="poster-container" @mouseover="showDetails = true" @mouseleave="showDetails = false">
            <img :src="getImageUrl(production.poster_path)" :alt="production.title">
            <div class="overlay" v-if="showDetails">
                <h3>{{ production.title || production.name }}</h3>
                <p>Titolo Originale: {{ production.original_title || production.original_name }}</p>
                <div id="language">
                    <p>Lingua:</p>
                    <p v-if="!getLangFlag(production.original_language)">{{ production.original_language }}</p>
                    <img v-else :src="getLangFlag(production.original_language)" :alt="production.original_language">
                </div>
                <div>
                    <p>Voto: {{ voteAverage }}/10</p>
                    <p><i v-for="i in 5" :key="i"
                            :class="{ 'fas fa-star': i <= starsCount, 'far fa-star': i > starsCount }"></i></p>
                </div>

                <p class="overview">Trama: {{ production.overview }}</p>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
.overview {
    overflow: auto;
}

h3 {
    font-size: 1.5rem;
}

p {
    margin: 0;
    font-size: 0.9rem;
}

#language {
    display: flex;
    align-items: center;
    gap: 10px;

    img {
        width: 25px;
        height: 15px;
    }
}

.col {
    position: relative;
}

.overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.900);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 5px;
    padding: 20px;
    opacity: 0;
    transition: opacity 1s;
}

.poster-container:hover .overlay {
    opacity: 1;
}
</style>