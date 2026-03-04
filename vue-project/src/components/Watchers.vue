<script setup>
import { ref, watch } from 'vue';

const message = ref('Hello, Vue 3 Watchers!');
const inputText = ref(' ')

// Watch for changes in the inputText and update the message accordingly

watch(inputText,(newValue, OldValue)=>{ 
    // You can perform some logic here when the inputText changes, such as updating the message or triggering other actions
    message.value = `you typed: ${newValue}`
    console.log(OldValue);
    console.log(newValue);
 })
</script>
<template>
  <h1>{{ message }}</h1>
  <input v-model="inputText" placeholder="Type Something..."/>
</template>