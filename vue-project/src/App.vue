<script setup>
  import SampleComponent1 from './components/SampleComponent1.vue';
import SampleComponent2 from './components/SampleComponent2.vue';
</script>

<template>
  <h1>Hello World</h1>
  <SampleComponent1/>
  <SampleComponent1/> 
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
    <SampleComponent2/>
  </p>
</template>

<style scoped></style>
