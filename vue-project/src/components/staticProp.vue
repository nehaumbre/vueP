<script setup>
import { ref } from 'vue';
const props = defineProps(['name'])
// console.log(props);
</script>
<template>
    <h1> static PROPS: {{ props.name }}</h1>
</template>