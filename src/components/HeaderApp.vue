<script>
import axios from 'axios';
import store from '../data/store.js';
export default {
    name: "HeaderApp",
    components: {


    },
    data() {

        return {
            store
        }
    },

    methods: {
        popularButton() {
            axios.get("https://api.themoviedb.org/3/tv/popular?api_key=cd9bb08e609470850f56a739b3e6641f").then(result => {

                this.store.movie = result.data.results
                console.log("APP MONTATA")
            });


        }
    },

    created() {

    },

    mounted() {
        axios.get("https://api.themoviedb.org/3/tv/popular?api_key=cd9bb08e609470850f56a739b3e6641f").then(result => {

            this.store.movie = result.data.results
            console.log("APP MONTATA")
        });

    }
}
</script>

<template>
    <!-- Navbar -->

    <nav class="navbar navbar-expand-lg navbar-light bg-transparent">
        <div class="container-fluid">
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <i class="fas fa-bars"></i>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <a class="navbar-brand mt-2 mt-lg-0" href="#">
                    <img src="../assets/img/pngwing.com.png" height="40" alt="MDB Logo" loading="lazy" />
                </a>
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link text-light" href="#">Film</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-light" href="#">Serie TV</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link text-light" href="#">Anime</a>
                    </li>
                    <li class="nav-item">
                        <a @click="popularButton" class="nav-link text-light" href="#">Popular</a>
                    </li>
                </ul>
            </div>

            <div class="d-flex align-items-center">
                <a class="text-reset me-3" href="#">
                    <i class="fas fa-shopping-cart"></i>
                </a>

                <div class="dropdown">
                    <a class="text-reset me-3 dropdown-toggle hidden-arrow" href="#" id="navbarDropdownMenuLink"
                        role="button" data-bs-toggle="dropdown" aria-expanded="false">
                        <i class="fas fa-bell"></i>
                        <span class="badge rounded-pill badge-notification bg-danger">1</span>
                    </a>
                    <ul class="dropdown-menu dropdown-menu-end bg-primary" aria-labelledby="navbarDropdownMenuLink">
                        <li><a class="dropdown-item text-light" href="#">Some news</a></li>
                        <li><a class="dropdown-item text-light" href="#">Another news</a></li>
                        <li><a class="dropdown-item text-light" href="#">Something else here</a></li>
                    </ul>
                </div>

                <div class="dropdown">
                    <a class="dropdown-toggle d-flex align-items-center hidden-arrow" href="#"
                        id="navbarDropdownMenuAvatar" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                        <img src="https://mdbcdn.b-cdn.net/img/new/avatars/2.webp" class="rounded-circle" height="25"
                            alt="Black and White Portrait of a Man" loading="lazy" />
                    </a>
                    <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdownMenuAvatar">
                        <li><a class="dropdown-item" href="#">My profile</a></li>
                        <li><a class="dropdown-item" href="#">Settings</a></li>
                        <li><a class="dropdown-item" href="#">Logout</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </nav>





</template>




<style></style>