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
        <button><i class="fa-solid fa-magnifying-glass"></i></button>
    </form>
</template>

<style lang="scss"scoped>
form {
    display: flex;
    gap: 20px;

    button {
        border: none;
        outline: none;
        background-color: transparent;
        position: absolute;
        right: 190px;
        top: 27px;
    }

    input {
        border: none;
        outline: none;
        border-radius: 20px;
        height: 20px;
        padding-left: 20px;
        position: relative;
        background-color: rgb(165, 165, 165);
    }
}
</style>