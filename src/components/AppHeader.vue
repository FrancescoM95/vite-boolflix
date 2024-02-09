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
            <a href="">
                <h1>Boolflix</h1>
            </a>
            <AppForm />
        </div>
    </header>
</template>
  
<style lang="scss">
header {
    background-color: #141414;
    height: 100px;
}

h1 {
    color: #D40000;
    margin-right: 60px;
    font-size: 3rem;
}

a {
    text-decoration: none;
}
</style>