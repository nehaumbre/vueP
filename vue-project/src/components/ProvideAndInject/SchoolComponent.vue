<script setup>
 import StudentComponent from './StudentComponent.vue'; 
//  defineProps(['studentName','studentAge','studentLocation'])
</script>
<template>
    <h1>School component(parent)</h1>
    <!-- <StudentComponent :studentName="studentName" :studentAge="studentAge" :studentLocation="studentLocation"/> -->
    <StudentComponent/>
</template>