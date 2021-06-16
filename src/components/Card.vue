<template>
    <div>
        <img :src="componeURL(item.poster_path)" alt="">
        <h3>{{item.title? item.title : item.name}}</h3>
        <h4>{{item.original_title ? item.original_title : item.original_name}}</h4>
        <img 
            src="../assets/images/it.png" 
            alt=""
            v-if="item.original_language == 'it'"
        >
        <img 
            src="../assets/images/en.png" 
            alt=""
            v-else-if="item.original_language == 'en'"
        >
        <p v-else>{{item.original_language}}</p>
        <p>{{item.vote_average}}</p>
    </div>
</template>

<script>
    export default{
        name: "Card",
        props : {
            "item": Object
        },
        methods:{
            componeURL : function(endUrl){
                //compone poster url
                const startUrl = "https://image.tmdb.org/t/p/w1280/"; 
                if (endUrl != null){
                    return  startUrl + endUrl; 
                }
            }
        }

    }
    
</script>


<style scoped>
img{
    width: 20px;
}
</style>
