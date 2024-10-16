<template>
     <div class="container">
        <div class="hero" :style="{ 'background-image': 'url(https://image.tmdb.org/t/p/w1280' + movieImgs + ')' }"></div>
        <img style="height: 250px" v-bind:src="'https://image.tmdb.org/t/p/w500' + movieDetails.data.poster_path" alt="cover" class="cover" />
        <p>{{ movieDetails.data.title }}</p>
        <p>ID is {{ movieId }}</p>
        <p>Release Date: {{ movieDetails.data.release_date }}</p>
        

</div> 
</template>

<script>
import axios from 'axios'

export default {
    props: {
        movieId: Number,
        movieDetails: {},
        movieImgs: String

    },

    data() {
        return {
            moreInfo: "",
            myMovieId: ""
        }
    },
    mounted() {
        console.log("more info id here" + this.movieId)
        //this.getMoreInfo(this.movieId) 
    },
    methods: {
        getMoreInfo() {
            // console.log("in api call" + movieId)
            axios
            .get("https://api.themoviedb.org/3/movie/" + "1174618" + "/credits?api_key=70aa7cf3c45a66892b6fc98973e73d66")
            .then((response) => {
                console.log(response)
            })
        }
    }
}

</script>

<style scoped>

p {
    color: black;
}
</style>