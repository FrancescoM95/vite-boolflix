<script>
import AppForm from './Form/AppForm.vue';
export default {
    name: 'AppHeader',
    components: { AppForm }
}
</script>

<template>
    <header>
        <div class="container">
            <h1>Boolflix</h1>
            <AppForm />
        </div>
    </header>
</template>
  
<style lang="scss">
header {
    background-color: #141414;
    padding: 10px 0;
    height: 140px;
}

h1 {
    color: #D40000;
}
</style>