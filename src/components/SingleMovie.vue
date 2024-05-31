<script>


export default {

    name: "SingleCard",
    props: {
        select: Object,
        url: String
        

    },
    data() {

        return {

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
    <div class="singleCard">
        <img :src="url + select.poster_path">
        <h2>{{ select.title }} {{ select.name }}</h2>
        <p class="language">{{ select.original_language }}</p>
        <p class="vote">{{ select.vote_average }}</p>
    </div>

</template>

<style scoped>
.singleCard {
    padding: 1rem;
    width: 15rem;
    background-color: rgba(30, 153, 210, 0.116);
    border: 1px solid black;
    font-size: 12px;
}

img {
    width: 100%;
}

.vote {
    color: rgb(9, 255, 0);
}

.language {
color: red;
}

h2 {
    font-size: 100%;
}
</style>
