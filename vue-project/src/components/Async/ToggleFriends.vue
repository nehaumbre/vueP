<script setup>
// import RenderFriends from './RenderFriends.vue';
const RenderFriends = defineAsyncComponent(()=> import('./RenderFriends.vue'))
import {ref, defineAsyncComponent} from 'vue';
let showFriends = ref(false)

const toggleFriends = ()=> showFriends.value =! showFriends.value
</script>
<template>
    <div v-if="showFriends"><RenderFriends/></div>  
    <button @click="toggleFriends">Toggle friends</button>  
</template>