// MILESTONE 3

<template>
    <main>
        <!-- MOVIES -->
        <div>
            <h2>Questi sono i film</h2>
        </div>
        <div class="container">
            <Media v-for="film in totalFilmsReserch" :key="film.id" :details="film"/>
        </div>

        

        <!-- MOVIES -->
        <div>
            <h2>Questi sono le serie tv</h2>
        </div>
        <div class="container">
            <Media v-for="serie in totalSerieReserch" :key="serie.id" :details="serie"/>
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
</style>
