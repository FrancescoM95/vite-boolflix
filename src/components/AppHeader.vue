<script>
import AppForm from './Form/AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm }
}
</script>

<template>
    <header>
        <div class="container d-flex justify-content-center gap-5 align-items-center h-100">
            <h1>Boolflix</h1>
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
    margin: 0;
}
</style>