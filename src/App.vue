
<template>
  <div id="app">
    <header>
      <Header @valueUserInput="apiCall" />
    </header>
    <main>
      <Main :totalFilmsReserch="filmDetails"/>
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
      apiKey: 'db9a08f20bbc721f9eb91b4003906b6b',
      userInputFilm: "",
    }
  },
  methods:  {
    apiCall: function (userInput){
      this.userInputFilm = userInput
      this.apiCallMovies()
    },
    apiCallMovies: function(){
      axios.get('https://api.themoviedb.org/3/search/movie',
      {
        params: {
          api_key: this.apiKey,
          query: this.userInputFilm
        }
      })
      .then((response) => {
        this.filmDetails = response.data.results
        console.log(this.filmDetails)
      });
    }
  }
}
</script>

<style lang="scss">
</style>
