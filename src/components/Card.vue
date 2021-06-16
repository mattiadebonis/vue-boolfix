<template>
    <div>
        <h3>{{item.title}}</h3>
        <h4>{{item.original_title}}</h4>
        <img 
            src="../assets/images/it.png" 
            alt=""
            v-if="item.original_language == 'it'"
        >
        <img 
            src="../assets/images/eng.png" 
            alt=""
            v-else-if="item.original_language == 'eng'"
        >
        <p v-else>{{item.original_language}}</p>
        <img src="" alt="">
        <p></p>

        <p>{{item.original_language}}</p>
        <p>{{item.vote_average}}</p>
    </div>
</template>

<script>
    export default{
        name: "Card",
        props : {
            "item": Object
        }
    }
    
</script>


<style scoped>
</style>
