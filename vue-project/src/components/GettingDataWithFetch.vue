<script setup>
import { ref } from 'vue';

const data = ref(null);

const fetchdata = ()=>{
    //make a fetch request using the fetch API
    fetch('https://jsonplaceholder.typicode.com/posts/9').then((response)=>{ 
        //Check if resonse is ok 2xx
        if(!response) { 
            throw new Error(`Network response was not ok ${response.status}`);
         }

         //Parse json response
         return response.json();
     }).then((responseData)=>{
        data.value = responseData;
     }).catch((error)=>{
        console.errror(`There was a problem with the fetch operation: ${error.message}`);
     })
}
</script>
<template>
    <h1>Getting Data with Fetch</h1>
    <p>This is a simple example of fetching data with the fetch API.</p>
    <button @click="fetchdata">FETCH_DATA</button>
    <h2>Data from API</h2>
    <pre>{{ data }}</pre>
</template>
