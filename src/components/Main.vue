<template>
    <main>
        <section 
            class="movies-container" 
            v-if="cards.lenght > 0"
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