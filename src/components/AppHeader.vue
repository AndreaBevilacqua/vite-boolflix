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

        setTitleFilter(term) {
            store.filter = term;
        },

        searchProductions() {
            if (!store.filter) {
                store.movies = [];
                store.series = [];
                return;
            }

            this.fetchApi("search/movie", 'movies');
            this.fetchApi("search/tv", 'series');
        },

        fetchApi(endpoint, collection) {

            const { baseUri, language, apiKey } = api;

            const params = {
                query: store.filter,
                api_key: apiKey,
                language
            }
            axios.get(`${baseUri}/${endpoint}`, { params })
                .then((res) => {
                    store[collection] = res.data.results;
                })
                .catch((err) => {
                    console.error(err)
                })
        }
    }
};
</script>

<template>
    <SearchBar @form-submit="searchProductions" @term-change="setTitleFilter" placeholder="Cerca film o serie tv"
        buttonLabel="Cerca" />
</template>

<style lang="scss"></style>
