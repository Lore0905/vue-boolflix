// MILESTONE 2
// Trasformiamo la stringa statica della lingua in una vera e propria bandiera della
// nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della
// nazione ritornata dall’API (le flag non ci sono in FontAwesome).
// Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca
// dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando
// attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di
// risposta diversi, simili ma non sempre identici)
// Qui un esempio di chiamata per le serie tv:
// https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=s
// crubs
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
