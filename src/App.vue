<script>
import { store } from './data/store'
import { api } from './data/index'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  name: 'Booflix',
  components: { AppHeader, AppMain },
  data: () => ({ store })
};
</script>

<template>
  <AppHeader />

  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>
