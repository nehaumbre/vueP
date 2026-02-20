<script setup>
// v-model is used in Vue.js to connect an input field to your data.
// 👉 It creates two - way binding
import { ref } from 'vue';

const formData = ref({username: '', email: '', passcode : ''})

</script>
<template>
    <h1>VMODEL</h1>
    <form @submit.prevent>
        <input  type="text" placeholder="username.." v-model="formData.username" >
        <button type="submit">Submit</button>
    </form>
    <h1>{{ formData.username }}</h1>
</template>