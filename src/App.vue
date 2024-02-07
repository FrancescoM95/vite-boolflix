<script >
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue'
export default {
  name: 'Boolflix',
  components: { AppMain, AppHeader }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss' as *;
</style>