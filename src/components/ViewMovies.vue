<template>
  <div id="container">
    <TopBar
    @genreMovies="receiveGenreIdEmit"
    />
    <div class="movieContainer" @click.self="closeModal()">
    <div class="mountedMovies" v-for="movie in movies" :key="movie.title">
      <p class="movieTitle">{{ movie.title }}</p>
      <img class="movieImg"
        style="height: 400px"
        v-bind:src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" @click="getMovieByID(movie.id)"
      />
    </div>
    <div class="movieInfoContainer" v-show="isMovieInfoVisible">
<MovieInfo 
@close="closeModal"
:movieDetails="movieInfo"
:movieImgs="movieImgs"
:movieId="movieID"
/>
</div>
</div>

  </div>
  
</template>

<script>
import axios from "axios";
import MovieInfo from './MovieInfo.vue';
import TopBar from "./TopBar.vue";


export default {

  components: {
    MovieInfo,
    TopBar
    
  },
    
  data() {
    return {
      isMovieInfoVisible: false,
      movies: [],
      movieImgs: "",
      url: "https://image.tmdb.org/t/p/w500",
      searchInput: "",
      movieInfo: "",
      movieID: "",
      parentGenreMovies: ""
    }
  },
  mounted() {
    this.getMovies();
  },
  methods: {

    getMovies() {
      if (this.searchInput == "") {

        axios
          .get(
            "http://localhost:8080/allMovies"
          )
          .then((response) => {
          console.log(response)
            this.movies = response.data.results;
            
          });
      } else if(this.searchInput != "") {

        axios
          .get(
            "https://api.themoviedb.org/3/search/movie?api_key=70aa7cf3c45a66892b6fc98973e73d66&query=" +
              this.searchInput
          )
          .then((response) => {
            this.movies = response.data.results;
          });
      } 
    },

    receiveGenreIdEmit(id) {
      this.parentGenreMovies = id
      console.log("Parent genre movies" + this.parentGenreMovies)
    },

    getMovieByID(movieID) {
      this.isMovieInfoVisible = !this.isMovieInfoVisible
      this.movieID = movieID
      console.log("movie id" + movieID)

      axios
      .get("http://localhost:8080/movieById?id=" + movieID)
      .then((response) => {
        this.movieInfo = response
        console.log("In view movies" + this.movieInfo.data)
      })
      
      axios
      .get("http://localhost:8080/movieImgsById?id=" + movieID)
      .then((response) => {
        this.movieImgs = JSON.stringify(response.data.backdrops[1].file_path).slice(1, -1)
        console.log("images" + this.movieImgs)
      })
    },

    closeModal() {
        this.isMovieInfoVisible = false
        this.movieImgs = ""
        this.movieInfo = ""
        
    }
  },
};
</script>

<style>

body {
  background-color: #282c34;
}

.movieInfoContainer {
  border-radius: 20px;
    flex-direction: column;
    background-position: center;
    position: fixed;
    background-color: black;
    top: 2%;
    background-size: cover;
}

#container {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.movieContainer {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 12px;
    align-content: center;
    justify-content: center;
}

p {
  color: white;
}

#searchBarContainer {
    align-self: center;
    margin-bottom: 30px;
}

#searchBar {
  width: 300px;
  height: 28px;
  border-radius: 20px;
  background-color: #322834;
  border: 1px, solid, black;
}

.movieImg {
  border-radius: 15px;
  transition: transform .2s;
}

.movieImg:hover {
  transform: scale(1.2);
}

.movieTitle {
  max-width: 30ch;
  max-height: 20px;
}

/* button {
  background-color: white;
  border-radius: 10px;
  margin-left: 8px;
  height: 30px;
  width: 60px;
} */
</style>

<!-- //CER 2.4k -->
