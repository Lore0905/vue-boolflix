Milestone 3:
In questa milestone come prima cosa aggiungiamo la copertina del film o della serie
al nostro elenco. Ci viene passata dall’API solo la parte finale dell’URL, questo
perché poi potremo generare da quella porzione di URL tante dimensioni diverse.
Dovremo prendere quindi l’URL base delle immagini di TMDB:
https://image.tmdb.org/t/p/ per poi aggiungere la dimensione che vogliamo generare
(troviamo tutte le dimensioni possibili a questo link:
https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400) per poi aggiungere la
parte finale dell’URL passata dall’API.
Esempio di URL:
https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png
Trasformiamo poi il voto da 1 a 10 decimale in un numero intero da 1 a 5, così da
permetterci di stampare a schermo un numero di stelle piene che vanno da 1 a 5,
lasciando le restanti vuote (troviamo le icone in FontAwesome).
Arrotondiamo sempre per eccesso all’unità successiva, non gestiamo icone mezze
piene (o mezze vuote :P)
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
</style>
