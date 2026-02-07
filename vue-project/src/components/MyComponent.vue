<script setup>
 const myMessage = "This is a Message"
 const myUpperCaseMessage = myMessage.toUpperCase()

 function add(x,y) {return  x+y} 
</script>

<template>
    <!-- Text Interpolation -->
    <h1>{{ myUpperCaseMessage }}</h1>
    <h2>{{2*2}}</h2> 
    <h3>{{ myMessage.length}}</h3>
    <p>Add 2 nos: {{ add(2,4) }}</p>
</template>

<style>

</style>