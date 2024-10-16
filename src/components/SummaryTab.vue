<template>
    <div class="container">

        <img style="height: 250px" v-bind:src="'https://image.tmdb.org/t/p/w500' + movieDetails.data.poster_path" alt="cover" class="cover" />
<div class="hero" :style="{ 'background-image': 'url(https://image.tmdb.org/t/p/w1280' + movieImgs + ')' }">
        
  <div class="details">
  
    <div class="titleOne"> {{ movieDetails.data.title }} <span class="rating">PG-13</span></div>

    <div class="title2">{{movieDetails.data.tagline}}</div>  

</div> 
  
</div> 

<div class="description">
  
  <div class="column1">
    <span class="tag">action</span>
    <span class="tag">fantasy</span>
    <span class="tag">adventure</span>
  </div> 
  
  <div class="column2">
    
    <p class="columnDesc"> {{ movieDetails.data.overview }}... <a href="#">read more</a></p>
    
  </div> 
</div>  
</div> 
</template>

<script>

export default {
    props: {
        movieId: Number,
        movieDetails: {},
        movieImgs: String

        
    },
    data() {
        return {
            isMovieInfoVisibleChild: false,
            tabs: []
        }
    },
   
    created() {
      this.tabs = this.$children
      
    },
    mounted() {
        console.log("in summary" + this.movieID)
        this.id = this.movieID
    },
    methods: {
        close() {
            this.isMovieInfoVisibleChild = !this.isMovieInfoVisibleChild
            this.$emit("close")
        }
    }
}

</script>


<style>

.tabs {
  margin-bottom: 35px;
}

*, *:before, *:after {
  box-sizing: border-box;
}

body {
  background: #43423E;
}

a {
  text-decoration: none;
  color: #5C7FB8
}

a:hover {
  text-decoration: underline;
}

.closeButton {
    width: 50px;
    margin-left: auto;
    margin-right: 0px;
}

.movie-card {
  font: 14px/22px;
  color: #A9A8A3;
  padding: 40px 0;
}

.container {
  margin: 0 auto;
  width: 780px;
  height: 600px;
  background: #F0F0ED;
  border-radius: 5px;
  position: relative;
}

.hero {
    margin-top: 35px !important;
  height: 342px;  
  margin:0;
  position: relative;
  overflow: hidden;
  z-index:1;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  transform: skewY(-2.2deg);
  transform-origin:0 0;
    
}

.cover {
  position: absolute;
  top: 160px;
  left: 40px;
  z-index: 2;
}

.details {
  padding: 190px 0 0 280px;
}
  
  
  .titleOne {
    color: white;
    font-size: 44px;
    margin-bottom: 13px;
    position: relative;
    
  }


  .title2 {    
    color: #C7C1BA;
    font-size: 23px;    
    font-weight: 300;
    margin-bottom: 15px;
  }
  
  
  .likes {
    margin-left: 24px;
  }
  
  
  .likes:before {
    content: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/195612/icon_like.png");
    position: relative;
    top: 2px;
    padding-right: 7px;
  }


.description {
  bottom: 0px;
  height: 200px;
  font-size: 16px;
  line-height: 26px;
  color: #B1B0AC;
  
}

.column1 {
  padding-left: 25px;
  padding-top: 80px;
  width: 220px;
  float: left;
  text-align: center;
}

.columnDesc {
    color: black;
}

.rating {
      position: absolute;
      top: 3px;
      margin-left: 12px;
      background: #C4AF3D;
      border-radius: 5px;
      color: #544C21;
      font-size: 14px;
      padding: 0px 4px;
      
    }

.tag {
  background: white;
  border-radius: 10px;
  padding: 3px 8px;
  font-size: 14px;
  margin-right: 4px;
  line-height: 35px;
  cursor: pointer;
}

.tag:hover {
  background: #ddd;
}

.column2 {
  color: black;
  padding-left: 41px;
  padding-top: 30px;
  margin-left: 20px;
  width: 480px;
  float: left;
}
  
  img:hover {
    opacity: 0.6;
  }
  

</style>
