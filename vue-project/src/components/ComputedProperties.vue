<script setup>
import { computed, ref } from 'vue';
const number = ref(9)

const counter = ref(0)

let squaredCounter = computed(()=> counter.value **2)



const counterIncrement = ()=>{ counter.value++ }

const squaredNumber = computed(()=>{ return number.value * number.value})

</script>
<template>
    <h1>Original number: {{ number }}</h1>
    <h1>Sqared number: {{ squaredNumber }}</h1>
    <p>
        Counter: {{ counter }}
        squaredCounter: {{ squaredCounter }}
        <button @click="counterIncrement">Increment Counter</button>
    </p>
</template>