<script setup>
defineProps({ name: { type: String, validator: (propValue) => { return ['John', 'alex', 'gin'].includes(propValue) } }, age:{type:Number, validator:(propValue)=>(propValue>=18)}, password:{type:String, validator: (propValue)=>(propValue.length>8)} })
</script>
<template>
    <h1>Custom Validator PROPS</h1>
    <h1>name: {{ name }}</h1>
    <h1>age: {{ age }}</h1>
    <h1>password :{{ password }}</h1>
</template>