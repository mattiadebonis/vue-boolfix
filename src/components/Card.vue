<template>
    <!-- card container-->
    <div class="card_container">
        <!-- card cover -->
        <div class="card_cover">
            <img 
                v-if="item.poster_path != null"
                :src="componeURL(item.poster_path)" alt=""             
                class="card_image"
            >
            <div v-else>
                <!-- empty cover -->
                <img  src="../assets/images/logo.png" alt="logo" class="no_cover">
            </div>
            
        </div>
        <!-- /card cover -->

        <!-- card info -->
        <div class="info_card">
            <!-- title -->
            <h3>{{item.title? item.title : item.name}}</h3>

            <!-- original title -->
            <p class="original_title">{{item.original_title ? item.original_title : item.original_name}}</p>

            <!-- language -->
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

            <!-- rating -->
            <div class="star_container">
                <i
                    v-for= "(n,index) in 5"
                    :key= "index" 
                    class="fas fa-star"
                    :class="getRating(item.vote_average,index)"
                ></i>
            </div>
            
            <!-- overview -->
            <p class="overview">{{item.overview}}</p>
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

        //function
        methods:{
            componeURL : function(endUrl){
            //compone poster url
                const startUrl = "https://image.tmdb.org/t/p/w1280/"; 
                if (endUrl != null){
                    return  startUrl + endUrl; 
                }
            },
            getRating : function(ratingTen, index){
                //get five star rating
                var ratingFive = (ratingTen/2).toFixed(0);
                if (index <= ratingFive){
                    return "star_yellow"
                }else{
                    return "star_none";
                }
            }
        },

    }
    
</script>


<style lang="scss" scoped>
    //import font awesome
    @import "~@fortawesome/fontawesome-free/css/all.min.css"; 
    //import variables
    @import "../assets/style/variable.scss";


    //card
    .card_container{
        width: 100%;
        position: relative;
        
        .card_image{
            width: 100%;
            overflow: hidden;
        }

        .no_cover{
            width:80%;
            margin:10%;
        }

        .info_card{
            opacity:0;
            color: white;
            position:absolute;
            top: 0px;
            padding: 25px;

            h3{
                font-size: 26px;
            }
            
            .original_title{
                color: lightgray;
            }

            .flag{
                width: 30px;
                margin-top: 15px;
            }

            .overview{
                font-size: 14px;
                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 3; /* number of lines to show */
                -webkit-box-orient: vertical;
            }   

            .star_container{
                margin-top: 15px;
                //color star

                .star_yellow{
                    color: rgb(255, 216, 0);
                 }

                .star_none{
                    display:none;
                }
            }
        }

        //switch from cover to info on mouse hover
        &:hover .card_cover {
            opacity:0;
            transition: $transition-card;
            width: 100%;
        }

        &:hover .info_card{
            opacity: 1;
            transition: $transition-card;
        }

    }
</style>
