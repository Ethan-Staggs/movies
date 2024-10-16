<template>
    <div id="searchBarContainer">
        <form class="searchForm" @submit.prevent="getSearchTerm">
            <input 
            id="searchBar" 
            type="text" 
            v-model="searchInput"
            />
            <button type="submit">Search</button>
        </form>
      
    </div>
  </template>
  
  <script>
    
  export default {

    data() {
        return {
            searchInput: ""
        }
    },
    methods: {
        getSearchTerm() {
            console.log("in other component" + this.searchInput)
             this.$emit("searchTerm", this.searchInput)
            
        }
    }
    
  }
  </script>
  
  <style>
  #searchBar {
    width: 300px;
    height: 28px;
    border-radius: 20px;
    background-color: #322834;
    border: 1px, solid, black;
  }

  button {
    height: 20px;
    width: 60px;
  }
  </style>