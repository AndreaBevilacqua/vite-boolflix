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


    }
};
</script>

<template>
    <div class="poster-img">
        <img :src="" :alt="title">
    </div>
    <ul>
        <li>{{ title }}</li>
        <li>{{ originalTitle }}</li>
        <li>
            <img v-if="HasFlag" :src="flagSrc" :alt="lang">
            <span v-else>{{ lang }}</span>
        </li>
        <li>{{ vote }}</li>
    </ul>
</template>

<style lang="scss">
img {
    max-width: 100px;
}
</style>
