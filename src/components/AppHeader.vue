<script>
import axios from 'axios';
import { store } from '../data/store';
import { api } from '../data/index';
import SearchBar from './SearchBar.vue';
export default {
    data: () => ({
        store,
        links: [
            {
                text: 'Home',
                url: '#',
            },
            {
                text: 'Serie Tv',
                url: '#',
            },
            {
                text: 'Film',
                url: '#',
            },
            {
                text: 'Originali',
                url: '#',
            },
            {
                text: 'Aggiunti di recente',
                url: '#',
            },
            {
                text: 'La mia lista',
                url: '#',
            },
        ]
    }),
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
                    store[collection] = res.data.results.map((p) => {
                        return {
                            id: p.id,
                            title: p.title || p.name,
                            originalTitle: p.original_title || p.original_name,
                            vote: p.vote_average,
                            lang: p.original_language,
                            posterPath: p.poster_path
                        }
                    })
                })
                .catch((err) => {
                    console.error(err)
                })
        }
    }
};
</script>

<template>
    <header>
        <div class="navbar">
            <img src="../assets/img/netflix.png" alt="netflix">
            <ul>
                <li v-for="link in links">{{ link.text }}</li>
            </ul>
        </div>

        <div class="search-bar">
            <SearchBar @form-submit="searchProductions" @term-change="setTitleFilter" placeholder="Cerca film o serie tv"
                buttonLabel="Cerca" />
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: rgb(15, 15, 15);
    padding: 20px;
    margin-bottom: 40px;

    display: flex;
    justify-content: space-between;
    align-items: center;
}

.navbar {
    display: flex;
    gap: 20px;
    align-items: center;

    ul {
        display: flex;
        gap: 11px;
    }
}
</style>
