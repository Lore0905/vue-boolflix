// Milestone 1:
// Creare un layout base con una searchbar (una input e un button) in cui possiamo
// scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il
// bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.
// Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni
// film trovato:
// 1. Titolo
// 2. Titolo Originale
// 3. Lingua
// 4. Voto
// ---------------------------------------------------------
 // 1  creo l'input type text
    // creo il button 
    // creo una variabile, nella quale salvo il dato scritto dall'utente, usando il v-model
    // lo passo all'App.vue CON l'emit 

    // guardare appunti App.vue
// ------------------------------------------------------------------
<template>
    <header>
        <div>
            <input type="text" v-model="userInput">
        </div>
        <div>
            <button @click="$emit ('valueUserInput', userInput) ">serch</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    
    data: function(){
        return {
            userInput: ""
        }
    }
}
</script>

<style scoped lang="scss">
header{
    border: 1px solid black;
    height: 100px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>