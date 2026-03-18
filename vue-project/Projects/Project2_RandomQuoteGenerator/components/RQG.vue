<template>
    <div class="quote-generator">
        <h1 class="app-title">Random Quote Generator</h1>
        <blockquote class="quote-container">
            <p v-if="loading">Loading...</p>
            <p v-else-if="data">{{ data.quote }}</p>
            <footer v-if="loading">-...</footer>
            <footer v-else-if="data">- {{ data.author }}</footer>
        </blockquote>
        <!-- <button @click="fetchRandomQuoteData" class="quote-button">Get Random Quote</button> -->
        <button @click="fetchRandomQuoteData" :disabled="loading" class="quote-button">
            {{ loading ? 'Loading...' : 'Get Random Quote' }}
        </button>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const data = ref(null);
const loading = ref(false);

const fetchRandomQuoteData = async () => {
    loading.value = true;
    try {
        //Make a get request using Axios
        const response = await axios.get(`https://dummyjson.com/quotes/random`);

        //Handle the response data
        data.value = response.data
    } catch (error) {
        console.error(`Error fetching data: ${error}`);
    } finally {
        loading.value = false;
    }
}
onMounted(() => {
    fetchRandomQuoteData();
});
</script>

<style scoped>
.quote-generator {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    text-align: center;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
    font-size: 24px;
    margin-bottom: 20px;
    color: #333;
}
.quote-container {
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 8px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
}
.quote-button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.quote-button:hover {
    background-color: #2980b9;
}

p {
    font-size: 18px;
    margin-bottom: 10px;
}

cite {
    font-style: normal;
    color: #777;
}
</style>
