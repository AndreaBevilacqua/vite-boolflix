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
    <div class="container">
        <section>
            <h2>FILM ORGINALI</h2>
            <CoverCard v-for="movie in store.movies" :key="movie.id" v-bind="movie" />
        </section>
        <section>
            <h2>SERIE ORIGINALI</h2>
            <CoverCard v-for="serie in store.series" :key="serie.id" v-bind="serie" />
        </section>
    </div>
</template>

<style lang="scss" scoped>
h2 {
    margin: 20px 0;
    font-size: 3rem;
}
</style>