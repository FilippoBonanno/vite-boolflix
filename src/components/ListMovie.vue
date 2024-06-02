<script>

import store from '../data/store.js';
import SingleMovie from './SingleMovie.vue';



export default {
    name: "ListMovie",
    components: {
        SingleMovie,

    },
    data() {

        return {
            store,
            urlImage: "https://image.tmdb.org/t/p/w780",
        }
    },

    methods: {


    },

    created() {

    },

    mounted() {

    }
}
</script>

<template>
    <div class="cardContainer">
        <SingleMovie v-for="film in this.store.movie" :select="film" :url="urlImage" />
    </div>

</template>

<style scoped>
.cardContainer {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;

}
</style>
