<script>
export default {
    name: 'SearchBar'
};
</script>

<template>
    <form>
        <input type="text" v-model.trim="term">
    </form>
</template>

<style lang="scss"></style>