<script setup>
import { reactive, watch, ref } from 'vue';

const state = reactive({ userName: 'Alex' })

//Multiple Sources example
const username = ref('Alex')
const counter = ref(0)

// When watching a property on a reactive object,
// we must use a getter function (not the property value directly

//() => state.userName is a getter function that returns the current value of state.userName.
watch(() => state.userName, (newValue, oldValue) => { console.log(`userName changed from ${oldValue} to ${newValue}`); })

//for multiple sources in watch
watch([username, counter], ([newUsername, newCounter], [oldUsername, oldCounter]) => {
  console.log(`username changed from ${oldUsername} to ${newUsername}`);
  console.log(`counter changed from ${oldCounter} to ${newCounter}`);
})
</script>
<template>
    <h1>Reactive Object Watchers Component</h1>
    <h2>{{ state.userName }}</h2>
    <button @click="state.userName = 'Jordan'">Change Name</button>
    <hr>
    <h1>{{ username }}</h1>
    <h2>{{ counter }}</h2>
    <button @click="username = 'Brick'">ChangeName</button>
    <button @click="counter++">Increment</button>
</template>