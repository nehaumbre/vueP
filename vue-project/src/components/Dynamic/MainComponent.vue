<template>
    <h1>Main Component</h1>
    <button @click="currentTab='ComponentOne'">One</button>
    <button @click="currentTab='ComponentTwo'">Two</button>
    <button @click="currentTab='ComponentThree'">Three</button>

    <!-- Dynamic Component -->
    <component :is="tabs[currentTab]" />
</template>

<script setup>
import { ref } from 'vue';
import ComponentOne from './ComponentOne.vue';  
import ComponentTwo from './ComponentTwo.vue';
import ComponentThree from './ComponentThree.vue';

const currentTab = ref('ComponentOne');
const tabs = {ComponentOne, ComponentTwo, ComponentThree};

</script>
