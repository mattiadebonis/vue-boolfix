<template>
    <main>
        <!-- movies -->
        <a href=""><h2>Film ></h2></a>
        <section 
            class="movies-container" 
            v-if="movieCards.length > 0 && searchedItem != ''"
        >
            <div class="card">
                <Card 
                    v-for = "card in movieCards"
                    :key = "card.id"
                    :item = "card"
                />
            </div>
        </section>
        <p class="no_found" v-else><i class="fas fa-film"></i> Nessun film trovato</p>
        <!-- /movies -->


        <!-- series -->
        <a href=""><h2>Serie ></h2></a>
        <section 
            class="series-container" 
            v-if="serieCards.length > 0 && searchedItem != ''"
        >
            <div class="card">
                
                    <Card 
                    v-for = "card in serieCards"
                    :key = "card.id"
                    :item = "card"
                    />     
            </div>
        </section>
        <p class="no_found" v-else><i class="fas fa-tv"></i> Nessuna serie trovata</p>
        <!-- /series -->
    </main>
</template>

<script>
    import Card from "./Card.vue";
    export default{
        name: "Main",
        components: {
            Card : Card
        },
        props:{
            "movieCards": Array,
            "serieCards": Array,
            "searchedItem":String
        }
    }
</script>


<style lang="scss" scoped>
@import "../assets/style/variable.scss";
main{
    width: 100%;
    margin-top: 60px;

    h2{
        color:white;
        text-transform: uppercase;
        margin: 10px;
        font-size: 14px;
        margin-top: 20px;
    }

    section{ 
        display: flex;
        width: 100%;
        .card{
           display: flex;
            div{
                width: calc(100vw/6);
            }       
        }
    }    

    .no_found{
        margin: 30px;
        color: gray;
        font-size: 24px;
    }
}
</style>