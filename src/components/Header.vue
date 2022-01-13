
<template>
    <header>
        <div id="title">
            <h1>BOOLFIX</h1>
        </div>
        <div id="input">
            <input type="text" v-model="userInput">
        </div>
        <div id="button">
            <button @click="$emit ('valueUserInput', userInput) "><i class="fas fa-search"></i></button>
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
    background-color: #141414;
    width: 100%;
    height: 70px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 5%;
    position: fixed;
    top: 0;
    z-index: 100;
    #title{
        flex-grow: 1;
        color: #E50914;
    }
    #input{
        margin: 0 30px;
        input{
            border: 0px;
            border-radius: 2px;
            padding: 2px 20px;
        }
    }
    #button{
        button{
            padding: 2px 20px;
            border-radius: 5px;
        }
    }
}

</style>