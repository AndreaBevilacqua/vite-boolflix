<script>
export default {
    name: 'SearchBar',
    data: () => ({ term: '' }),
    props: {
        buttonLabel: String,
        placeHolder: String
    },
    emits: ['form-submit', 'term-change']
};
</script>

<template>
    <form @submit.prevent="$emit('form-submit')">
        <input type="text" @keyup="$emit('term-change', term)" v-model.trim="term" :placeholder="placeHolder">
        <button>{{ buttonLabel }}</button>
    </form>
</template>

<style lang="scss"></style>