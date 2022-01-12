// MILESTONE 2 
// creare un if sulla li lingua
    // se element.original_language === 'it'  || element.original_language === 'en'
    // stampa ../../src/assets/' + element.original_language + '.png'
    // altriemnti element.original_language
<template>
    <main>
        <!-- TITLE -->
        <div v-for="(element, index) in totalFilmsReserch" :key="index" class="square">
            <ul>
                <li>
                    <h5>TITLE</h5>
                </li>
                <li >
                    {{element.title}}
                </li>
            <!-- TITOLO ORIGINALE -->
                <li>
                    <h5>TITOLO ORIGINALE</h5>
                </li>
                <li >
                    {{element.original_title}}
                </li>
            <!-- LINGUA -->
                <li>
                    <h5>LINGUA</h5>
                </li>
                <li >
                    <div v-if="element.original_language === 'it'  || element.original_language === 'en'" >
                        <img :src= "require( '../../src/assets/' + element.original_language + '.png')" >
                    </div>
                    <div v-else>
                        {{element.original_language}}
                    </div>
                </li>
            <!-- VOTO -->
                <li>
                    <h5>VOTO</h5>
                </li>
                <li>
                    {{element.vote_average}}
                </li>
            </ul>
        </div>
        
    </main>
</template>

<script>
export default {
    name: "Main",
    props: {
    totalFilmsReserch: Array
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

</style>
