<script setup>
import { ref } from 'vue';
const username = ref('')
const email = ref('')
const password = ref('')
</script>
<template>
    <!-- 
    Component Event
    - send child component data to parent component
    - allows child Components to emit events(custom events) 
    that can be listened by parent components
    Child
    $emit - triggers a custom event that carries data 
    that you wanna send to parent
    Parent
    - you can use v-on directive(@) to listen
     to custom event emitted by child 
    -->
    <h1>Form Component</h1>
    <form @submit.prevent ="$emit('userinfo', username,email,password)">
        <input type="text" placeholder="username" v-model="username">
        <input type="email" placeholder="email"  v-model="email">
        <input type="password" placeholder="password"  v-model="password">
        <button type="submit">Submit</button>
    </form>
</template>