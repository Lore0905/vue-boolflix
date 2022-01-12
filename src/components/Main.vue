// MILESTONE 2 
// creo la funzione apiCallSeries
// faccio la chiamata HTTP --> usando axios 
// uso i seguenti parameti obbligatori:
// api_key
// query
// creo l' arrey serieDetails nei data 
// nella funzione .then() --> scrivo che serieDetails deve essere uguale a response.data.results
// con una props lo passo al componente main
// inserisco i rispettivi dati
<template>
    <main>
        <!-- MOVIES -->
        <div>
            <h2>Questi sono i film</h2>
        </div>

        <!-- TITLE -->
        <div v-for="(film, index) in totalFilmsReserch" :key="index" class="square film">
            
            <ul>
                <li>
                    <h5>TITLE</h5>
                </li>
                <li >
                    {{film.title}}
                </li>
            <!-- TITOLO ORIGINALE -->
                <li>
                    <h5>TITOLO ORIGINALE</h5>
                </li>
                <li >
                    {{film.original_title}}
                </li>
            <!-- LINGUA -->
                <li>
                    <h5>LINGUA</h5>
                </li>
                <li >
                    <div v-if="film.original_language === 'it'  || film.original_language === 'en'" >
                        <img :src= "require( '../../src/assets/' + film.original_language + '.png')" >
                    </div>
                    <div v-else>
                        {{film.original_language}}
                    </div>
                </li>
            <!-- VOTO -->
                <li>
                    <h5>VOTO</h5>
                </li>
                <li>
                    {{film.vote_average}}
                </li>
            </ul>
        </div>

        <!-- MOVIES -->
        <div>
            <h2>Questi sono le serie tv</h2>
        </div>
        
        <!-- TITLE -->
        <div v-for="(serie, index) in totalSerieReserch" :key="index" class="square serie">
            <ul>
                <li>
                    <h5>TITLE</h5>
                </li>
                <li >
                    {{serie.name}}
                </li>
            <!-- TITOLO ORIGINALE -->
                <li>
                    <h5>TITOLO ORIGINALE</h5>
                </li>
                <li >
                    {{serie.original_name}}
                </li>
            <!-- LINGUA -->
                <li>
                    <h5>LINGUA</h5>
                </li>
                <li >
                    <div v-if="serie.original_language === 'it'  || serie.original_language === 'en'" >
                        <img :src= "require( '../../src/assets/' + serie.original_language + '.png')" >
                    </div>
                    <div v-else>
                        {{serie.original_language}}
                    </div>
                </li>
            <!-- VOTO -->
                <li>
                    <h5>VOTO</h5>
                </li>
                <li>
                    {{serie.vote_average}}
                </li>
            </ul>
        </div>
        
    </main>
</template>

<script>
export default {
    name: "Main",
    props: {
    totalFilmsReserch: Array,
    totalSerieReserch: Array
  }
 }
</script>

<style scoped lang="scss">
main{
    height: calc(100vh - 100px);
    border: 1px solid black;
    display: flex;
    justify-content: space-evenly;
    align-content: flex-start;
    flex-wrap: wrap;
    text-align: center;
       .square{
           border: 1px solid black;
           width: 150px ;
           height: 170px;
           margin: 20px;
            ul{
                margin: 0;
                padding: 0;
                li{
                    list-style-type: none;
                    h5{
                        margin: 3px 0;
                    }
                    img{
                        width: 20px;
                    }
                }
            }
       }
}
.film{
    background-color: chocolate;
}
.serie{
    background-color: cornflowerblue;
}
</style>
