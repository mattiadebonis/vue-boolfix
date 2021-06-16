<template>
    <main>
        <section 
            class="movies-container" 
            v-if="movieCards.length > 0"
        >
            <h2>Film</h2>
            <div class="movies">
                <Card 
                    v-for = "card in movieCards"
                    :key = "card.id"
                    :item = "card"
                />
            </div>
        </section>
        <section 
            class="movies-container" 
            v-if="serieCards.length > 0"
        >
            <h2>Serie</h2>
            <div class="movies">
                <Card 
                    v-for = "card in serieCards"
                    :key = "card.id"
                    :item = "card"
                />
            </div>
        </section>
        <h1 v-else>Nessun elemento</h1>
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
            "serieCards": Array
        }
        
    }
</script>


<style scoped>

</style>