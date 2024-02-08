<script>
export default {
    name: 'CoverCard',
    props: {
        production: Object
    }
};
</script>

<template>
    <ul>
        <li>{{ production.title || production.name }}</li>
        <li>{{ production.original_title || production.original_name }}</li>
        <li>{{ production.original_language }}</li>
        <li>{{ production.vote_average }}</li>
    </ul>
</template>

<style lang="scss"></style>
