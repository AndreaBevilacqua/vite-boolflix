<script>
import { store } from '../data/store';
import CoversContainer from './CoversContainer.vue';
export default {
    name: 'AppMain',
    components: { CoversContainer },
    data: () => ({ store })
};
</script>

<template>
    <section>
        <h2>Movies</h2>
        <ul v-for="movie in store.movies" :key="movie.id">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </section>
</template>

<style lang="scss"></style>