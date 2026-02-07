<script setup>
// const myChannel = "https://www.youtube.com/watch?v=pgWZLS75Nmo"
// const amazingImage = 'https://images.unsplash.com/photo-1699646034253-0ebaa551d226?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
// const alttext = "Couples"
// const imgWidth = 400
// const imgHeight = 400

// * Dynamic Binding
const imgCouple = {  
    src : 'https://images.unsplash.com/photo-1699646034253-0ebaa551d226?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    alt: 'Just a random Image',
    width : 300,
    height: 300
}
</script>

<template>
    <!-- <a v-bind:href="myChannel">youtube</a> Old way-->
    <!-- <a :href="myChannel">youtube</a> 
    <img :src="amazingImage" :alt="alttext" :width="imgWidth" :height="imgHeight">  -->
    <img :="imgCouple"></img>
</template>
<style>
</style>