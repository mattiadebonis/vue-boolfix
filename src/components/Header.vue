<template>
    <header>
        <!-- left header --> 
        <div class="left_header">
            <!-- logo -->
            <a href="#">
                <img src="../assets/images/logo.png" alt="" class="logo">
            </a>
            <!-- menu -->
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Serie TV</a></li>
                <li><a href="#">Originali</a></li>
                <li><a href="#">Aggiunti di recente</a></li>
                <li><a href="#">La mia lista</a></li>
            </ul>
            <!-- /menu -->
        </div>
        <!-- /left header -->
            
        <!-- right header -->
        <div class="right_header">
            <input 
                v-model="searchText" 
                v-on:input="$emit('performSearch', searchText)" 
                type="text" 
                placeholder="Cerca film"
            >
        </div>
        <!-- /right header -->
        
    </header>
</template>

<script>
    export default{
        name: "Header",  
        //data
        data: function(){
            return{
                searchText : ""
            }
        },
    }
</script>


<style lang="scss" scoped>
    header{
        width: 100vw;
        height: 70px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        //left header
        .left_header{
            display: flex;
            align-items: center;
            .logo{
                width: 120px;
                margin:15px;
            }
            ul{
                list-style: none;
                display: inline-block;
            }
            li{
                display: inline;
                margin: 15px;
                a{
                    color:white;
                    text-decoration:none;
                    font-size: 16px;
                }
            }
        }

        //right header
        .right_header{
            padding: 30px;
        
            input{
                width: 250px;
                height: 35px;
                margin: 15px;
                padding-left: 15px;
                border: none;
                border-radius: 5px;
                font-size: 14px;
                color:gray;
            }
            
        
        }
    }
</style>