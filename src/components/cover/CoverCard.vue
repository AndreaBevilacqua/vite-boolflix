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
    <img class="poster" :src="posterSrc" :alt="title">
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

<style lang="scss"scoped>
.poster {
    width: 100%;
    object-fit: contain;
    height: 400px;
    width: 300px;
    margin-right: 10px;
    transition: transform 450ms;

    &:hover {
        transform: scale(1.08)
    }
}

ul {
    display: none;
}
</style>
