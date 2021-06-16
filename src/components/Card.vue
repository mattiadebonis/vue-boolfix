<template>
    <div>
        <h3>{{item.title}}</h3>
        <h4>{{item.original_title}}</h4>
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
