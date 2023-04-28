<script setup>
    import q from "./data/quizes.json"
    import { ref, watch } from "vue";

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
            <div v-for="quiz in quizes" :key="quiz.id" class="card">
                <img :src=quiz.img alt="">
                <div class="card-text">
                    <h2>{{quiz.name}}</h2>
                    <p>{{ quiz.questions.length }} questions</p>
                </div>
            </div>
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

    .card {
        width: 210px;
        overflow: hidden;
        border-radius: 5%;
        box-shadow: 1px 1px 10px rgba(0,0,0,0.5);
        margin-bottom: 35px;
        margin-right: 20px;
        cursor: pointer;
    }
   

    .card img {
        width: 100%;
        margin: 0;
    }

    .card .card-text{
        padding: 0 5px;
        margin-bottom: 5px;
    }

    .card .card-text h2 {
        font-weight: bold;
    }

    .cards-container{
        display: flex;
        flex-wrap: wrap;
        margin-top: 40px;
        justify-content: space-around;
    }

</style>