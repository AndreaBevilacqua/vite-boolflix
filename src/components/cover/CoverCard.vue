<script>
import { pics } from '../../data/index'
export default {
    name: 'CoverCard',
    props: {
        id: Number,
        title: String,
        originalTitle: String,
        vote: Number,
        lang: String,
        posterPath: String || null
    },
    computed: {
        HasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.lang);
        },

        flagSrc() {
            const url = new URL(`../../assets/img/${this.lang}.png`, import.meta.url);
            return url.href;
        },

        posterSrc() {
            return this.posterPath ? pics.baseUri + this.posterPath : pics.placeholder
        },

        vote() {
            return Math.round(this.vote / 2)
        }
    }
};
</script>

<template>
    <div class="poster-img">
        <img :src="posterSrc" :alt="title">
    </div>
    <ul>
        <li>{{ title }}</li>
        <li>{{ originalTitle }}</li>
        <li>
            <img v-if="HasFlag" :src="flagSrc" :alt="lang">
            <span v-else>{{ lang }}</span>
        </li>
        <li><i v-for="n in 5" :key="n" class="fa-star" :class="n <= vote ? 'fas' : 'far'"></i></li>
    </ul>
</template>

<style lang="scss">
img {
    max-width: 100px;
}
</style>
