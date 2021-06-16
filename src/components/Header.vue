<template>
    <div>
        <input 
            v-model="searchText" 
            type="text" 
            placeholder="Cerca film"
        >

        <button 
            @click="$emit('performSearch', searchText)" 
        >Cerca</button>
    </div>
</template>

<script>
    export default{
        name: "Header",  
        data: function(){
            return{
                searchText : ""
            }
        },
        

    }
</script>


<style scoped>

</style>