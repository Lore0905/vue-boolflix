// 2 salvo il valore dato dall'utente in una variabile
  // creo la funzione APICALL --> dove sarà presente la chiamata HTTP --> effettuata tramite la libreria Axios
  // creo le rispettive Query var (Titolo (con la variabile precedentemente creata), TitoloOriginale, Lingua, Voto)
  // salvo le informazioni in un oggetto
  // tramite una promps la invio al main e la stampo
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
      filmDetails: []
    }
  },
  methods:  {

    apiCall: function(userInput){
      axios.get('https://api.themoviedb.org/3/search/movie',
      {
        params: {
          api_key: 'db9a08f20bbc721f9eb91b4003906b6b',
          query: userInput
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
