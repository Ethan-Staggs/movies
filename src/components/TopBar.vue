<template>

    <div class="sideBarContainer">
        
        <img class="catLogo" src="./icons8-cat-50.png">
        

    <div class="imageContainer">
        <img class="topBarImg" src="./icons8-home-50.png" style="width: 30px; height: 30px;">
        <div class="homeText">Home</div>
        </div>

        <div class="imageContainer">
        <img class="topBarImg" src="./icons8-search-50.png" style="width: 30px; height: 30px;">
        <div class="searchText">Search</div>
        <div id="search">
            <!-- <search-bar /> -->
        </div>
        </div>

        <div class="imageContainer">
        <img class="topBarImg" src="./icons8-movie-50.png" style="width: 30px; height: 30px;">
        <div class="movieText">Movies</div>
        </div>

        <div class="imageContainer">
        <img class="topBarImg" src="./icons8-tv-50.png" style="width: 30px; height: 30px;">
        <div class="tvText">TV Shows</div>
        </div>

        <div class="imageContainer" @click="openDropDown()">
        <img class="topBarImg" src="./icons8-menu-50.png" style="width: 30px; height: 30px;">
    
        <div class="genreText">Genres</div>
        <div id="dropDown">
            <p v-for="genre in genres" :key="genre.id" v-bind="genre.id" @click="emitGenreId(genre.id)">{{genre.name}}</p>
            <p></p>
        </div>

        </div>

        </div>

        
    </template>


<script>
 import axios from 'axios';
// import SearchBar from './SearchBar.vue';


export default {
    data() {
        return {
            genres: [
    {
      "id": 28,
      "name": "Action"
    },
    {
      "id": 12,
      "name": "Adventure"
    },
    {
      "id": 16,
      "name": "Animation"
    },
    {
      "id": 35,
      "name": "Comedy"
    },
    {
      "id": 80,
      "name": "Crime"
    },
    {
      "id": 99,
      "name": "Documentary"
    },
    {
      "id": 18,
      "name": "Drama"
    },
    {
      "id": 10751,
      "name": "Family"
    },
    {
      "id": 14,
      "name": "Fantasy"
    },
    {
      "id": 36,
      "name": "History"
    },
    {
      "id": 27,
      "name": "Horror"
    },
    {
      "id": 10402,
      "name": "Music"
    },
    {
      "id": 9648,
      "name": "Mystery"
    },
    {
      "id": 10749,
      "name": "Romance"
    },
    {
      "id": 878,
      "name": "Science Fiction"
    },
    {
      "id": 10770,
      "name": "TV Movie"
    },
    {
      "id": 53,
      "name": "Thriller"
    },
    {
      "id": 10752,
      "name": "War"
    },
    {
      "id": 37,
      "name": "Western"
    }
  ],
  genreId: "",
  genreMovies: []
        }
        
    },
    methods: {
        openDropDown() {
            let drop = document.getElementById("dropDown");

            if(drop.style.display == "none") {
                drop.style.display = "block";
            } else {
                drop.style.display = "none";
            }
        },
        emitGenreId(id) {
          this.genreId = id
          axios
          .get("https://api.themoviedb.org/3/discover/movie?api_key=70aa7cf3c45a66892b6fc98973e73d66&with_genres=" + 35)
          .then((response) => {
            this.genreMovies = response.data.results
            console.log("child Movie by genre " + this.genreMovies)
          })
          
            console.log("child " + id)
            this.$emit("genreMovies", this.genreMovies)
        },
        getGenreMovies() {
          // axios
          // .get("https://api.themoviedb.org/3/discover/movie?api_key=70aa7cf3c45a66892b6fc98973e73d66&with_genres=" + this.genreId)
          // .then((response) => {
          //   console.log("Movie by genre " + response)
          // })
        }
        // openSearch() {
        //     let search = document.getElementById("search");

        //     if(search.style.display == "none") {
        //         search.style.display = "block";
        //     } else {
        //         search.style.display = "none";
        //     }
        // }

    }
}

</script>

<style>

#dropDown {
  display: none;
  border-radius: 20px;
  position: absolute;
  background-color: #282c34;
  min-width: 160px;
  overflow: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

#search {
 display: none;
 position: absolute;
 display: flex;
 flex-direction: column;
 align-items: center;
 justify-content: center;
 align-self: center;
    
}

.dropdown-content p {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.sideBarContainer {
  padding: 30px;
    background-color: black;
    border-radius: 20px;
    width: 100%;
    height: 70px;
    display: flex;
    gap: 55px;
    top: 0px;
    position: sticky;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-bottom: 20px; 
}

.catLogo {
    align-self: center;
}
</style>