
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