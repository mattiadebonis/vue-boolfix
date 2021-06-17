<template>
  <div id="app">

    <!-- import searched film -->
    <Header @performSearch="search"/>
    
    <Main 
      :movieCards="movies"
      :serieCards="series"
    />
  </div>
</template>

<script>
  import axios from "axios";
  import Header from "./components/Header.vue";
  import Main from "./components/Main.vue";
  export default {
    name: 'App',
    
    // components
    components: {
      Header: Header,
      Main : Main
    },

    //data
    data: function(){
      return{
        apiUrl: "https://api.themoviedb.org/3/search/",
        apiKey : "519ec88cceb49e7cc957ef9c3c309ffd",
        movies : [],
        series : []
      }
      
    },

    //function
    methods :{
      search: function(text){
        //extract and save into an array the searched movies

        const paramsObj = {
          params:{
                api_key: this.apiKey,
                query: text,
                language: "it-IT"
              }
        };
        //axios movies call
        axios
          .get(this.apiUrl + 'movie', paramsObj)
          .then(
            (res) =>{
              this.movies = res.data.results;
            }
          )
          .catch(
            (err) =>{
              console.log("Error", err);
            }
          );
        //axios series call
        axios
          .get(this.apiUrl + 'tv', paramsObj)
          .then(
            (res) =>{
              this.series = res.data.results;
            }
          )
          .catch(
            (err) =>{
              console.log("Error", err);
            }
          );

      }
    }
  }
</script>

<style lang="scss">
  *{
    box-sizing:border-box;
    margin: 0;
    padding: 0;
  }
  body{
    background-color: black;
  }
  #app{
    width: 100vw;
    width: 100vh;
  }





</style>
