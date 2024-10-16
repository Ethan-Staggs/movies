<template>

<div class="movie-card">
  

  <div class="tabs">
      <movie-info-tabs>
        <movie-info-tab title="Summary">
          <summary-tab 
          :movieId="movieId"
          :movieDetails="movieDetails"
          :movieImgs="movieImgs"
          />
        </movie-info-tab>

        <movie-info-tab title="More Info">
          <more-info-tab
          :movieId="movieId"
          :movieDetails="movieDetails"
          :movieImgs="movieImgs"
          />
        </movie-info-tab>

        <movie-info-tab title="Tickets">
          <where-to-watch-tab/>
        </movie-info-tab>

      </movie-info-tabs>

    </div>

  
</div> 
    
</template>

<script>
import MovieInfoTabs from './MovieInfoTabs.vue'
import MovieInfoTab from './MovieInfoTab.vue'
import SummaryTab from './SummaryTab.vue'
import MoreInfoTab from './MoreInfoTab.vue'
import WhereToWatchTab from './WhereToWatchTab.vue'


export default {

  components: {
    MovieInfoTabs,
    MovieInfoTab,
    MoreInfoTab,
    SummaryTab,
    WhereToWatchTab
  },
  props: {
    movieDetails: {},
    movieId: Number,
    movieImgs: String
    
  },
  mounted() {
    console.log("in movieInfo " + this.movieId)
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