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
    <div class="card">
        <img class="poster" :src="posterSrc" :alt="title">
        <ul class="overlay">
            <li>{{ title }}</li>
            <li>{{ originalTitle }}</li>
            <li>
                <img v-if="HasFlag" :src="flagSrc" :alt="lang">
                <span v-else>{{ lang }}</span>
            </li>
            <li><i v-for="n in 5" :key="n" class="fa-star" :class="n <= vote ? 'fas' : 'far'"></i></li>
        </ul>
    </div>
</template>

<style lang="scss"scoped>
.fas {
    color: rgb(255, 217, 0);
}

.card {
    position: relative;
    width: 25%;

    .overlay {
        position: absolute;
        bottom: 0;
        left: 17px;
        right: 17px;
        background-color: rgba(0, 0, 0, 0.5);
        overflow: hidden;
        height: 0;
        transition: .5s ease;
    }
}

.card:hover .overlay {
    height: 50%;
}

.poster {
    display: block;
    object-fit: contain;
    height: 400px;
    width: 300px;
    transition: transform 450ms;
}

ul {
    display: flex;
    flex-direction: column;
    gap: 10px;
    justify-content: center;
    padding-left: 20px;

    img {
        max-width: 60px;
    }
}
</style>
