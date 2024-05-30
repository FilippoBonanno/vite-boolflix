<script>

import store from './data/store.js';
import axios from 'axios';
import SingleMovie from './components/SingleMovie.vue';



export default {

    components: {
        SingleMovie

    },
    data() {

        return {
            store,
            urlImage: "https://image.tmdb.org/t/p/w500"
        }
    },

    methods: {
        // FACCIAMO LA CHIAMATA AXIOS DELL'API E METTIAMOLO IN UNA FUNZIONE
        getMovie() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: { query: 'dragon', include_adult: 'false', language: 'en-US', page: '1' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjZDliYjA4ZTYwOTQ3MDg1MGY1NmE3MzliM2U2NjQxZiIsInN1YiI6IjY2NTdhNGUwYWU3N2NlNDI2MWM0NjYxMSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.xHruwl1ntwpw8uLvgauW9vbT13VI6NNCOmSgs5mYrWY'
                }
            };

            axios
                .request(options)
                .then( (response) => {
                    // INSERIAMO L'API DULLO STORE
                    this.store.movie = response.data.results
                    console.log(this.urlImage + store.movie[0].backdrop_path);
                })
                .catch(function (error) {
                    console.error(error);
                });
        }


    },

    created() {



    },

    mounted() {
        this.getMovie();
    }
}
</script>

<template>
    <h1>NETFLIX</h1>
    <div class="container">
        <p>container</p>
    </div>

    <div>
       <img :src="this.urlImage + store.movie[0].backdrop_path" >

    </div>
    <SingleMovie/>

</template>

<style scoped></style>
