

<template>
    <main>
        <!-- MOVIES -->
        <div v-if="totalFilmsReserch.length > 0">
            <h2>Questi sono i film</h2>
        </div>
        <div class="container">
            <Media v-for="film in totalFilmsReserch" :key="film.id" :details="film" :type="'movie'"/>
        </div>

        

        <!-- SERIE -->
        <div v-if="totalSerieReserch.length > 0">
            <h2>Questi sono le serie tv</h2>
        </div>
        <div class="container">
            <Media v-for="serie in totalSerieReserch" :key="serie.id" :details="serie" :type="'tv'"/>
        </div>
        
        <div v-if="totalSerieReserch.length === 0" class="alert">
            cerca il film che vuoi vedere
        </div>
        
        
    </main>
</template>

<script>
import Media from '../components/Media.vue'

export default {
    name: "Main",
    components: {
        Media
    },
    props: {
    totalFilmsReserch: Array,
    totalSerieReserch: Array
    },
  
}
</script>

<style scoped lang="scss">
main{
    margin-top: 100px;
    // title
    h2{
        text-align: left;
        margin: 2% 2%;
    }
}
.alert{
    font-size: 20px;
    padding: 50px;
}
</style>
