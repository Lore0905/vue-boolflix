<template>
    <main>
        <!-- TITLE -->
        <ul>
            <li>
                <h1>TITLE</h1>
            </li>
            <li v-for="(element, index) in totalFilmsReserch" :key="index">
                {{element.title}}
            </li>
        </ul>
        <!-- TITOLO ORIGINALE -->
        <ul>
            <li>
                <h1>TITOLO ORIGINALE</h1>
            </li>
            <li v-for="(element, index) in totalFilmsReserch" :key="index">
                {{element.original_title}}
            </li>
        </ul>
        <!-- LINGUA -->
        <ul>
            <li>
                <h1>LINGUA</h1>
            </li>
            <li v-for="(element, index) in totalFilmsReserch" :key="index">
                {{element.original_language}}
            </li>
        </ul>
        <!-- VOTO -->
        <ul>
            <li>
                <h1>VOTO</h1>
            </li>
            <li v-for="(element, index) in totalFilmsReserch" :key="index">
                {{element.vote_average}}
            </li>
        </ul>
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
    justify-content: space-around;
    text-align: center;
        ul{
            li{
                list-style-type: none;
            }
        }
}

</style>
