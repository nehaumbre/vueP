<script setup>
// basic validation in props below
// const props = defineProps({ fullname: String, age: Number })

//complex prop validation

const props = defineProps({ fullname: { default: 'Guest',required: true, type: String}, age: Number})
</script>
<template>
    <h1>PROPS validation</h1>
    <hr>
    <h1>{{ props.fullname }}</h1>
    <h1>{{ props.age }}</h1>
</template>