<template>
    <div>
        <div class="wrapping">
            <div class="square" @mouseenter="getCast()">
                <!-- background -->
                <div class="background-path" v-if="details.poster_path !==  null">
                    <img :src="'https://image.tmdb.org/t/p/w300' + details.poster_path" alt="">
                </div>
                <!-- TITLE -->
                <ul>
                    <li>
                        <h5>TITLE</h5>
                    </li>
                    <li >
                        {{details.title ? details.title : details.name}}
                    </li>
                <!-- TITOLO ORIGINALE -->
                    <li>
                        <h5>TITOLO ORIGINALE</h5>
                    </li>
                    <li >
                        {{details.original_title ? details.original_title : details.original_name}}
                    </li>
                <!-- LINGUA -->
                    <li>
                        <h5>LINGUA</h5>
                    </li>
                    <li >
                        <div v-if="flagsAvailable.includes(details.original_language)" class="flag">
                            <img :src= "require( '../../src/assets/' + details.original_language + '.png')" >
                        </div>
                        <div v-else>
                            {{details.original_language}}
                        </div>
                    </li>
                <!-- VOTO -->
                    <li>
                        <h5>VOTO</h5>
                    </li>
                    <li>
                        {{star(details.vote_average)}}
                        <i class="fas fa-star" v-for=" n in numberOfStars " :key="n"></i>
                        <i class="far fa-star" v-for=" n in (5 - numberOfStars)" :key="n"></i>
                    </li>
                <!-- CAST -->
                    <li>
                        <h5>CAST</h5>
                    </li>
                    <template v-if="chooseTheMediaCast(this.type).length > 0">
                        <li v-for="(name, index) in chooseTheMediaCast(this.type)" :key="name.cast_id">
                            <div v-if="index < 5 ">
                                {{name.name}}
                            </div>
                        </li>
                    </template >
                    <div v-else>
                        Mi dispiace, mai il cast non è disponibile
                    </div>
                    <!-- GENERE ASSOCIATO -->
                    <li>
                        <h5>GENERE</h5>
                    </li>
                    <li v-for="(genre, index) in chooseTheMediaGenres(this.type)" :key="genre.id">
                        <div v-if="index < 5 ">
                            {{genre.name}}
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Media',
    props:{
        details: Object,
        type: String
    },
    data: function(){
        return{
            numberOfStars: 0,
            flagsAvailable: ['it', 'en'],
            apiKey: 'db9a08f20bbc721f9eb91b4003906b6b',
            movieCast: [],
            serieCast: [],
            movieGenres: [],
            serieGenres: []
        }   
    },
    methods: {
        //   creo una funzione che mi permetta di stampare a schermo le stelle in base al voto
        //  il voto lo passo alla funzione come argomento 
        star: function(voto) {
        const roundedVote = Math.ceil(voto / 2) ;
        this.numberOfStars = roundedVote 
        
        return this.numberOfStars
        },
        getCast: function(){
            if (this.type === 'movie'){
                this.getCastFilm()
                this.getGenresMovie()
            }
            if (this.type === 'tv') {
                this.getCastSerie(),
                this.getGenresSerie()
            }
        },
        // CHIAMATA HTTP PER PRENDERE IL CAST
        getCastFilm: function (){
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}/credits`,
            {
                params: {
                api_key: this.apiKey,
                }
            })
            .then((response) => {
                this.movieCast = response.data.cast
                console.log(this.movieCast)
            });
        },
        getCastSerie: function (){
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}/credits`,
            {
                params: {
                api_key: this.apiKey,
                }
            })
            .then((response) => {
                this.serieCast = response.data.cast
                console.log(this.serieCast)
            });
        },
        chooseTheMediaCast: function (tipo){
            if(tipo === 'movie'){
                return this.movieCast
            }
            else if (tipo === 'tv'){
                return this.serieCast
            }
        },
        // CHIAMATA HTTP PER PRENDERE I GENERI
        getGenresMovie: function(){
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}`,
            {   
                params: {
                api_key: this.apiKey,
                }
            })
            .then((response) => {
                this.movieGenres = response.data.genres
                console.log(this.movieCast)
            });
        },
        getGenresSerie: function(){
            axios.get(`https://api.themoviedb.org/3/${this.type}/${this.details.id}`,
            {   
                params: {
                api_key: this.apiKey,
                }
            })
            .then((response) => {
                this.serieGenres = response.data.genres
                console.log(this.serieGenres)
            });
        },
        chooseTheMediaGenres: function (tipo){
            if(tipo === 'movie'){
                return this.movieGenres
            }
            else if (tipo === 'tv'){
                return this.serieGenres
            }
        },
    },
}
</script>

<style lang="scss" scoped>
.square{
    width: 342px;
    min-height: 550px;
    margin: 20px 5px;
    position: relative;
    flex-shrink: 0;
    background-color: rgba($color: #000000, $alpha: 0.3);

    .background-path{ 
        img{
        width: 100%;
        height: 100%;
        position: absolute;
        object-fit: cover;
        } 
    } 
    ul{
        margin: 0;
        padding: 10% 20px;
        
        li{
            h5{
                margin: 3px 0;
                padding: 5px 0px;
                font-size: 15px;
                color: #E50914;
            }
            .flag{
                img {
                width: 20px;
                
                }
            }
        }
    }
}

// HOVER
.square:hover{
    transform: scale(1.04);
    z-index: 10;
}
.square:hover .background-path{
    display: none;
}
</style>