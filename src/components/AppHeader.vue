<script>
import AppForm from './Form/AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm }
}
</script>

<template>
    <header>
        <div class="container d-flex justify-content-center align-items-center h-100">
            <a href="https://fontmeme.com/it/font-netflix/"><img src="https://fontmeme.com/permalink/240417/b56b6dbf16d8b13130b87655a06e056d.png" alt="font-netflix" border="0"></a>
            <AppForm />
        </div>
    </header>
</template>
  
<style lang="scss">
header {
    background-color: #141414;
    height: 100px;
}

a {
    text-decoration: none;
    margin-right: 10px;
}
</style>