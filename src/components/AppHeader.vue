<script>
import { store } from '../data/store'
import SearchBar from './SearchBar.vue';
export default {
    data: () => ({ store }),
    name: 'AppHeader',
    components: { SearchBar },
    methods: {
        searchMovies() {
            console.log(store.filter)
        },
        setTitleFilter(term) {
            store.filter = term;
        }
    }
};
</script>

<template>
    <SearchBar @form-submit="searchMovies" @term-change="setTitleFilter" placeholder="Cerca film o serie tv"
        buttonLabel="Cerca" />
</template>

<style lang="scss"></style>
