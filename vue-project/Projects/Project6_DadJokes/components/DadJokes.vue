<script setup>
import axios from 'axios';
import { ref } from 'vue';

const joke = ref('');

const fetchJoke = async()=>{  
    try{  
        const response = await axios.get("https://icanhazdadjoke.com/", {  
            headers: {  
                Accept: "application/json"
            }
        }) 
        joke.value = response.data.joke
    }catch(error){  
        console.error("Error fetching dad joke:", error)
    }
}
</script>
<template>
    <div class="dad-jokes-container">
        <div class="title-row">
            <h2 class="dad-jokes-title">Dad Jokes</h2>
            <span class="badge">Powered by icanhazdadjoke</span>
        </div>
        <button @click="fetchJoke" class="get-joke-button">Get Dad Joke</button>
        <div v-if="joke" class="dad-joke" aria-live="polite">{{ joke }}</div>        
    </div>
</template>
<style scoped>
.dad-jokes-container {
  max-width: 520px;
  margin: 2rem auto;
  padding: 1.5rem;
  border-radius: 20px;
  background: linear-gradient(135deg, #f8d7e9 0%, #fedea8 45%, #d6e4ff 100%);
  border: 1px solid rgba(102, 126, 234, 0.45);
  box-shadow: 0 20px 35px rgba(59, 130, 246, 0.18);
  color: #1f2937;
  font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  text-align: center;
}
.title-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.75rem;
  margin-bottom: 1rem;
}
.dad-jokes-title {
  margin: 0;
  font-size: 1.7rem;
  letter-spacing: 0.02em;
  color: #111827;
}
.badge {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  background: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(165, 180, 252, 0.4);
  color: #3730a3;
  padding: 0.2rem 0.5rem;
  border-radius: 999px;
}
.get-joke-button {
  margin: 0.5rem 0 1rem;
  border: none;
  border-radius: 999px;
  background: linear-gradient(130deg, #f472b6 0%, #a78bfa 50%, #67e8f9 100%);
  color: #111827;
  font-weight: 800;
  letter-spacing: 0.01em;
  padding: 0.65rem 1.35rem;
  cursor: pointer;
  transition: transform 0.15s ease, box-shadow 0.2s ease;
}
.get-joke-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 18px rgba(165, 243, 252, 0.35);
}
.get-joke-button:active {
  transform: translateY(0);
}
.dad-joke {
  margin: 0 auto;
  margin-top: 0.5rem;
  border-radius: 16px;
  background: #ffffff;
  border: 1px solid #a5f3fc;
  padding: 1rem 1rem;
  font-size: 1.02rem;
  line-height: 1.5;
  color: #111827;
  min-height: 3rem;
  box-shadow: 0 8px 18px rgba(30, 64, 175, 0.12);
}
.dad-joke::before {
  content: "\201C";
  font-size: 1.6rem;
  color: #f472b6;
  vertical-align: top;
  margin-right: 0.2rem;
}
.dad-joke::after {
  content: "\201D";
  font-size: 1.6rem;
  color: #a78bfa;
  margin-left: 0.2rem;
}
@media (max-width: 640px) {
  .dad-jokes-container {
    margin: 1rem;
    padding: 1rem;
  }
  .dad-jokes-title {
    font-size: 1.4rem;
  }
}
</style>
