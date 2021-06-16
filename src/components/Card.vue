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
        <p>{{getRating(item.vote_average)}}</p>
        
        <img 
            v-for= "(item, index) in ratingItem"
            :key= "index"
            src="../assets/images/star-solid.svg"
            alt=""
        >
        
    </div>
</template>

<script>
    export default{
        name: "Card",
        //components
        props : {
            "item": Object
        },

        //data 
        data: function(){
            return{
                i : 0,
                ratingItem: []
            }
        },

        //function
        methods:{
            componeURL : function(endUrl){
                //compone poster url
                const startUrl = "https://image.tmdb.org/t/p/w1280/"; 
                if (endUrl != null){
                    return  startUrl + endUrl; 
                }
            },
            getRating : function(ratingTen){
                this.ratingItem = []
                var ratingFive
                ratingFive = (ratingTen/2).toFixed(0);
                for(var i=0; i<ratingFive; i++){
                    this.ratingItem.push("");
                }
                console.log(this.ratingItem)
            }
        }

    }
    
</script>


<style scoped>
img{
    width: 20px;
}
</style>
