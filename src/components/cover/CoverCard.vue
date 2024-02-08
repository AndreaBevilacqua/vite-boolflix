<script>
export default {
    name: 'CoverCard',
    props: {
        production: Object
    },
    computed: {
        HasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.production.original_language);
        },

        flagSrc() {
            const url = new URL(`../../assets/img/${this.production.original_language}.png`, import.meta.url);
            return url.href;
        }
    }
};
</script>

<template>
    <ul>
        <li>{{ production.title || production.name }}</li>
        <li>{{ production.original_title || production.original_name }}</li>
        <li>
            <img v-if="HasFlag" :src="flagSrc" :alt="production.original_language">
            <span v-else>{{ production.original_language }}</span>
        </li>
        <li>{{ production.vote_average }}</li>
    </ul>
</template>

<style lang="scss">
img {
    max-width: 100px;
}
</style>
