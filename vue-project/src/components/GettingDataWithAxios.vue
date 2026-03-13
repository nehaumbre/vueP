<script setup>
import { ref } from 'vue';
import axios from 'axios';

const data = ref(null);

const fetchData = async() => {  
    try {
        //Make a get request using Axios
        const response = await axios.get(`https://jsonplaceholder.typicode.com/posts`);

        //Handle the response data
        data.value = response.data
    } catch (error) {
        console.error(`Error fetching data: ${error}`);
    }
}
</script>
<template>
    <h1>Getting Data with Axios</h1>
    <button @click="fetchData">Fetch Data</button>
    <pre>{{ data }}</pre>
</template>