<script setup>
import { ref } from 'vue';
let count = ref(0)

const submitHandler = (e) => { 
    e.preventDefault();
    alert('Valid Credentials')
}

const IncrementbyFive = ()=> {count.value += 5}
const DecrementbyFive = ()=>  {count.value -= 5}

const showMessage = (message) => {alert(message)}

</script>
<template>
    <h1>Count : {{ count }}</h1>
     <!-- above code [let count = 0] wont work because we need to make count reactive in Vue js 
      What is reactivity?: It means framework automatically updates UI  when information 
      behind it changes.Its a  core concept that allows you to create dynamic and responsive apps
      without manually manipulating the DOM
      How do we achieve reactivity in Vue JS?
      - reactive() -ref() for reactive state
      -->
    <button v-on:click="count++">Increment</button>
    <!-- v-on is one way to attach events other is @-->
    <button @:click="count--">Decrement</button>
    <button @:click="IncrementbyFive">Increment-by-5</button>
    <button @:click="DecrementbyFive">Decrement-by-5</button>

    <form @:submit="submitHandler">
        <input type="email" placeholder="Pease enter your Email..">
        <input type="password" placeholder="Enter password">
        <button type="submit">Log in</button>
    </form>

    <button @click="showMessage('This is my message to you ')">Show Messsage</button>
</template>