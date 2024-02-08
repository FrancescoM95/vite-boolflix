<script>
export default {
    name: 'AppCard',
    props: {
        production: Object
    },
    methods: {
        getLangFlag(lang) {
            return (lang === 'it' || lang === 'en') ? ('../../src/assets/img/' + lang + '.png') : '';
        },
        getImageUrl(posterPath) {
            return posterPath ? `https://image.tmdb.org/t/p/w342${posterPath}` : 'https://via.placeholder.com/342x513?text=No+Image';
        }

    }
}
</script>

<template>
    <div class="col">
        <div id="title">
            <h3>{{ production.title || production.name }}</h3>
        </div>
        <img :src="getImageUrl(production.poster_path)" :alt="production.title">
        <p>Titolo Originale: {{ production.original_title || production.original_name }}</p>

        <div id="language">
            <p>Lingua:</p>
            <p v-if="!getLangFlag(production.original_language)">{{ production.original_language }}</p>
            <img v-else :src="getLangFlag(production.original_language)" :alt="production.original_language">
        </div>
        <p>Voto: {{ production.vote_average }}</p>
    </div>
</template>

<style lang="scss">
h3 {
    font-size: 1.5rem;
}

p {
    margin: 0;
}


#title {
    height: 90px;
    margin-top: 35px;
    display: flex;
    align-items: center;
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
</style>