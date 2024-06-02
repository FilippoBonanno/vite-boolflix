<script>


export default {

    name: "SingleCard",
    props: {
        select: Object,
        url: String



    },
    data() {

        return {
            imgPlaceholder: "https://ih1.redbubble.net/image.1861329650.2941/flat,750x,075,f-pad,750x1000,f8f8f8.jpg"

        }
    },

    methods: {
        getLanguage(lingua) {
            if (lingua == "it") {
                return this.it
            } else {
                return this.en

            }
        },

        getFlag(language) {
            if (language == "it") {
                return "https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1280px-Flag_of_Italy.svg.png"

            } else {

                return "https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/1920px-Flag_of_the_United_Kingdom_%283-5%29.svg.png"
            }
        },

        getVote(vote) {
            return (Math.round(vote / 2));
        },

        getStars(vote, condiction) {

            let newVote = this.getVote(vote)
            let classe = 'fa-regular fa-star';
            if (newVote >= condiction) {
                classe = 'fa fa-star';
            }

            return classe;
        },



    },

    created() {

    },

    mounted() {

    }
}
</script>

<template>
    <div class="singleCard">
        <img v-if="select.poster_path" :src="url + select.poster_path">
        <img v-else :src="imgPlaceholder">
        <h2>{{ select.title }} {{ select.name }}</h2>
        <div>
            <img class="flag" :src="getFlag(select.original_language)">
            <p class="vote">{{ getVote(select.vote_average) }}</p>
            <span class="star"><i :class="getStars(select.vote_average, 1)"></i></span>
            <span class="star"><i :class="getStars(select.vote_average, 2)"></i></span>
            <span class="star"><i :class="getStars(select.vote_average, 3)"></i></span>
            <span class="star"><i :class="getStars(select.vote_average, 4)"></i></span>
            <span class="star"><i :class="getStars(select.vote_average, 5)"></i></span>
        </div>

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
    height: 18rem;
}

.vote {
    margin-top: 1rem;
    color: rgb(9, 255, 0);
}

.language {
    color: red;
}

h2 {
    margin-top: 1rem;
    font-size: 100%;
}

.flag {
    width: 15%;
    height: 5%;
}

.star {
    color: gold;
}

.hidden {
    display: none;
}

.singleCard:hover {
    cursor: pointer;
}
</style>
