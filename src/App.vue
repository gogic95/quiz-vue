<script setup>
    import q from "./data/quizes.json";
    import { ref, watch } from "vue";
    import Card from "./components/card.vue";

    const quizes = ref(q);
    const search = ref("");

    watch(search, () => {
        quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
    })
    
</script>

<template>
    <div class="container">
        <header>
            <h1>Quizes</h1>
            <input v-model.trim="search" type="text" placeholder="Search">
        </header>
        <div class="cards-container">         
            <Card v-for="quiz in quizes" 
                    :key="quiz.id"                
                    :img = quiz.img
                    :name = quiz.name
                    :questions = quiz.questions
                
            />
        </div>
    </div>
</template>


<style scoped>
    
    .container{
        max-width: 1000px;
        margin: 0 auto;
    }

    header{
        margin-bottom: 10px;
        margin-top: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    header h1 {
        font-weight: bold;
        margin-right: 30px;
    }

    header input {
        border: none;
        background-color: rgba(128,128,128,0.1);
        padding: 10px;
        border-radius: 9px;
    }

    .cards-container{
        display: flex;
        flex-wrap: wrap;
        margin-top: 40px;
        justify-content: space-around;
    }

</style>