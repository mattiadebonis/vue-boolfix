<template>
    <main>
        <section 
            class="movies-container" 
            v-if="cards.length > 0"
        >
            <h2>Film</h2>
            <div class="movies">
                <Card 
                    v-for = "card in cards"
                    :key = "card.id"
                    :item = "card"
                />
            </div>
        </section>
        <h1 v-else>Nessun elemento trovato</h1>
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
            "cards": Array
        }
        
    }
</script>


<style scoped>

</style>