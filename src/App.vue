<script>

import store from './data/store.js';
import axios from 'axios';
import ListMovie from './components/ListMovie.vue';



export default {

    components: {
        ListMovie

    },
    data() {

        return {
            store,
            urlImage: "https://image.tmdb.org/t/p/w780",
            apiMovieUrl: "https://api.themoviedb.org/3/search/movie?api_key=cd9bb08e609470850f56a739b3e6641f&query=",
            apiSeriesTV: "https://api.themoviedb.org/3/search/tv?api_key=cd9bb08e609470850f56a739b3e6641f&language=it_IT&query=",
            userInput: ""

        }
    },

    methods: {
        searchButton() {
            axios.get(this.apiMovieUrl + this.userInput).then(result => {

                this.store.movie = result.data.results
                console.log("APP MONTATA")
            });

            axios.get(this.apiSeriesTV + this.userInput).then(result => {

                this.store.movie = result.data.results
                console.log("APP MONTATA")
            });
            this.userInput = ""
        }



    },

    created() {



    },

    mounted() {

    }

}
</script>

<template>
    <h1>NETFLIX</h1>
    <div class="container">
        <div class="input-group mb-3">
            <input v-model="userInput" type="text" class="form-control" placeholder="Cerca Film o SerieTV"
                aria-label="Recipient's username" aria-describedby="button-addon2">
            <button @click="searchButton" class="btn btn-outline-secondary" type="button"
                id="button-addon2">Cerca</button>
        </div>

        <ListMovie />
    </div>

</template>

<style scoped></style>
