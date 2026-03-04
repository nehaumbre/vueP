<script setup>
import { ref } from 'vue';
const count = ref(10);

const plus = () => count.value++
const minus = () => count.value--

//script setup is private by default
// A parent referencing a child cant access anything
//expose all properties and methods first then we can use it in parent component
defineExpose({ count, plus, minus })
</script>
<template>
    <h1>Ref Component</h1>
    <p>Count: {{ count }}</p>
    <button @click="plus">+</button>
    <button @click="minus">-</button>
</template>