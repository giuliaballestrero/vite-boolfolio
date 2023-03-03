<script>
import AppHeader from './components/AppHeader.vue';

export default {

  name: 'AppVue',

  components: {
    AppHeader,
  }
}

</script>

<template>

  <AppHeader/>

  <!-- Aggiungo il componente router view alla struttura principale -->
  <router-view></router-view>

</template>

<style lang="scss">
@use './styles/general.scss' as *;

</style>
