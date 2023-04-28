<template>
    <div class="card">
        <img :src=img alt="">
        <div class="card-text">
            <h2>{{name}}</h2>
            <p>{{ questions.length }} questions</p>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        img:{
            type: String,
            required: true,
            default: ""
        },
        name:{
            type: String,
            required: true,
            default: ""
        },
        questions:{
            type: Array,
            required: true,
            default: () => []
        },
    })
</script>

<style scoped>
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


</style>
