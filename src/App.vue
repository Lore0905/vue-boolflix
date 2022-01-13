
<template>
  <div id="app">
    <header>
      <Header @valueUserInput="apiCall" />
    </header>
    <main>
      <Main :totalFilmsReserch="filmDetails" :totalSerieReserch="serieDetails"/>
    </main>
  </div> 
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function (){
    return {
      filmDetails: [],
      serieDetails: [],
      apiKey: 'db9a08f20bbc721f9eb91b4003906b6b',
      userInput: "",
    }
  },
  methods:  {
    apiCall: function (userInput){
      this.userInput = userInput
      this.apiCallMovies()
      this.apiCallSerie()
    },
    apiCallMovies: function(){
      axios.get('https://api.themoviedb.org/3/search/movie',
      {
        params: {
          api_key: this.apiKey,
          query: this.userInput
        }
      })
      .then((response) => {
        this.filmDetails = response.data.results
        console.log(this.filmDetails)
      });
    },
    apiCallSerie: function(){
      axios.get('https://api.themoviedb.org/3/search/tv',
      {
        params: {
          api_key: this.apiKey,
          query: this.userInput
        }
      })
      .then((response) => {
        this.serieDetails = response.data.results
        console.log(this.serieDetails)
      });
    }
  }
}
</script>

<style lang="scss">
@import './style/variables.scss';
@import './style/general.scss';
@import './style/common.scss';
body{
  font-family: 'Roboto', sans-serif;
  background-color: #141414;
  color: white;
}
::-webkit-scrollbar{
  background-color:#141414;
}
::-webkit-scrollbar-thumb{
  background-color: white;
  border-radius: 10px;
  display: none;
}
body:hover ::-webkit-scrollbar-thumb{
  display: block;
}
</style>
