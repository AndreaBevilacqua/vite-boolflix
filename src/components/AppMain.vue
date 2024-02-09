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
            <h2>FILM </h2>
            <div class="row-posters">
                <CoverCard v-for="movie in store.movies" :key="movie.id" v-bind="movie" />
            </div>
        </section>
        <section>
            <h2>SERIE </h2>
            <div class="row-posters">
                <CoverCard v-for="serie in store.series" :key="serie.id" v-bind="serie" />
            </div>
        </section>
    </div>
</template>

<style lang="scss" scoped>
h2 {
    margin: 20px 0;
    font-size: 3rem;
}

h3 {
    text-align: center;
    font-size: 3rem;
}

.row-posters {
    display: flex;
    overflow-y: hidden;
    overflow-x: scroll;
    padding: 20px;

    &::-webkit-scrollbar {
        display: none;
    }
}
</style>