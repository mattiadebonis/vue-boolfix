<template>
    <div>
        <h3>{{item.title}}</h3>
        <p>Ciaos</p>
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