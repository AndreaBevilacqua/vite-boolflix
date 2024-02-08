<script>
import axios from 'axios';
import { store } from '../data/store';
import { api } from '../data/index';
import SearchBar from './SearchBar.vue';
export default {
    data: () => ({ store }),
    name: 'AppHeader',
    components: { SearchBar },
    methods: {
        searchMovies() {
            if (!store.filter) {
                store.movies = [];
                return;
            }

            const { baseUri, language, apiKey } = api;

            const params = {
                query: store.filter,
                api_key: apiKey,
                language
            }

            axios.get(`${baseUri}/search/movie`, { params })
                .then((res) => {
                    store.movies = res.data.results;
                })
                .catch((err) => {
                    console.error(err)
                })
        },

        setTitleFilter(term) {
            store.filter = term; t
        }
    }
};
</script>

<template>
    <SearchBar @form-submit="searchMovies" @term-change="setTitleFilter" placeholder="Cerca film o serie tv"
        buttonLabel="Cerca" />
</template>

<style lang="scss"></style>
