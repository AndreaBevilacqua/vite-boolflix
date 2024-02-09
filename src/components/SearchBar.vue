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
        right: 275px;
        top: 28px;

        i {
            color: white;
            margin: 0 15px;
            font-size: 1.5rem;
        }
    }

    input {
        border: 2px solid white;
        outline: none;
        height: 40px;
        line-height: 40px;
        padding-left: 28px;
        position: relative;
        background-color: rgb(0, 0, 0);
        color: white;
    }
}
</style>