<script setup>
import {ref} from 'vue';
const friends = ref(['alex','john','jordan','Kim','sarah'])
</script>
<template>
    <h3 v-for="(friend,i) in friends" :key="i">{{ friend }}</h3>
</template>