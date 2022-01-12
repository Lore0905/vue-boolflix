// MILESTONE 3

<template>
    <main>
        <!-- MOVIES -->
        <div>
            <h2>Questi sono i film</h2>
        </div>

        <div class="film-wrapping">
            <div v-for="(film, index) in totalFilmsReserch" :key="index" class="square film">
                <!-- background -->
                <div class="background-path" v-if="film.poster_path !==  null">
                    <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt="">
                </div>
                <!-- TITLE -->
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
                        <div v-if="film.original_language === 'it'  || film.original_language === 'en'" class="flag">
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
                        {{star(film.vote_average)}}
                        <i class="fas fa-star" v-for=" n in numberOfStars " :key="n"></i>
                    </li>
                </ul>
            </div>
        </div>

        <!-- MOVIES -->
        <div>
            <h2>Questi sono le serie tv</h2>
        </div>
        
        <!-- TITLE -->
        <div class="serie-wrapping">
            <div v-for="(serie, index) in totalSerieReserch" :key="index" class="square serie">
                <!-- background -->
                <div class="background-path" v-if="serie.poster_path !==  null">
                    <img :src="'https://image.tmdb.org/t/p/w300' + serie.poster_path" alt="">
                </div>
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
                        <div v-if="serie.original_language === 'it'  || serie.original_language === 'en'" class="flag">
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
                    <li >
                        {{star(serie.vote_average)}}
                        <i class="fas fa-star" v-for=" n in numberOfStars " :key="n"></i>
                    </li>
                </ul>
            </div>
        </div>
        
    </main>
</template>

<script>
export default {
    name: "Main",
    props: {
    totalFilmsReserch: Array,
    totalSerieReserch: Array
  },
  data: function(){
      return{
        numberOfStars: 0,
    }
  },
  methods: {
    //   creo una funzione che mi permetta di stampare a schermo le stelle in base al voto
    //  il voto lo passo alla funzione come argomento 
        star: function(voto) {
        const roundedVote = Math.ceil(voto / 2) ;
        this.numberOfStars = roundedVote 
        
        return this.numberOfStars
        }
    }
}
</script>

<style scoped lang="scss">
main{
    // height: calc(100vh - 100px);
       .square{
           width: 350px;
           min-height: 500px;
           margin: 20px;
           position: relative;
           
           .background-path{ 
                img{
                width: 100%;
                height: 100%;
                position: absolute;
                object-fit: cover;
                display: none;
                } 
            } 
            ul{
                margin: 0;
                padding: 20px 10px;
                
                li{
                    
                    h5{
                        margin: 3px 0;
                        padding: 5px 0px;
                    }
                    .flag{
                        img {
                        width: 20px;
                        
                        }
                    }
                }
            }
        }
}

// wrapping
.serie-wrapping, .film-wrapping{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
// single details
.film{
    background-color: chocolate;
}
.serie{
    background-color: cornflowerblue;
}
h2{
    text-align: center;
}
     
</style>
