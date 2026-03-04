<template>
  <div>
    <button @click="counter.decrement">-</button>
    <span style="margin:0 1rem">{{ counter.count }}</span>
    <button @click="counter.increment">+</button>
  </div>
</template>

<script setup>
// import { ref } from 'vue';
// const count = ref(0);

// const increment = () => {
//   count.value++;
// };

// const decrement = () => {
//   count.value--;
// };
import { useCounter } from '@/shared/useCounter';
const counter = useCounter()
</script>
