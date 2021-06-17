<template>
    <!-- card container-->
    <div class="card_container">
        <!-- card cover -->
        <div class="card_cover">
            <img :src="componeURL(item.poster_path)" alt=""             class="card_image">
        </div>
        <!-- /card cover -->

        <!-- card info -->
        <div class="info_card">
            <h3>{{item.title? item.title : item.name}}</h3>
            <p class="original_title">{{item.original_title ? item.original_title : item.original_name}}</p>
            <img 
                src="../assets/images/it.png" 
                alt=""
                v-if="item.original_language == 'it'"
                class="flag"
            >
            <img 
                src="../assets/images/en.png" 
                alt=""
                v-else-if="item.original_language == 'en'"
                class="flag"
            >
            <p v-else>{{item.original_language}}</p>
            <p>{{getRating(item.vote_average)}}</p>
            
            <img 
                v-for= "(item, index) in ratingItem"
                :key= "index"
                src="../assets/images/star-solid.svg"
                alt=""
                class="flag"
            >
        </div>
        <!-- /card info -->
    </div>
    <!-- /card container-->

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
            }
        },

    }
    
</script>


<style lang="scss" scoped>

//card
.card_container{
    width: 100%;
    position: relative;

    .card_image{
        width: 100%;
    }
    .info_card{
        opacity:0;
        color: white;
        position:absolute;
        top: 0px;
        padding: 15px;
        h3{
            font-size: 24px;
        }
        .original_title{
            font-size: 8px;
        }
        .flag{
            width: 30px;
            margin-top: 15px;
        }   
    }

    //switch from cover to info on mouse hover
    &:hover .card_image{
        opacity:0;
        transition: opacity 0.2s;
        width: 100%;
    }
    &:hover .info_card{
        opacity: 1;
        transition: opacity 0.2s;
    }
}
</style>
