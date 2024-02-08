<script>
import { store } from '../data/store';
import CoverCard from './cover/CoverCard.vue';
export default {
    name: 'AppMain',
    components: { CoverCard },
    data: () => ({ store })
};
</script>

<template>
    <section>
        <h2>Movies</h2>
        <CoverCard v-for="movie in store.movies" :key="movie.id" :production="movie" />
    </section>
    <section>
        <h2>Series</h2>
        <CoverCard v-for="serie in store.series" :key="serie.id" :production="serie" />
    </section>
</template>

<style lang="scss"></style>