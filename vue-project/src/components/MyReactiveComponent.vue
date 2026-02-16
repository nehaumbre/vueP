<script setup>
import { reactive } from 'vue';

// let initialState = reactive(0)
// in reactive we are not allowed to work on primitive data types 
//thats why line `let initialState = reactive(0)` doesnt work 
let initialState = reactive({count : 0})

let newInitialState = reactive({value:{count:0}, user: ['Hyakman', 'Moore']})

const changeUser = ()=>{  
    newInitialState.user[0] = 'White'
    newInitialState.user[1] = 'Doomi'
}
</script>

<template>
    <!-- <h1>Count: {{initialState}}</h1>
    <button @click="initialState++">+</button> -->
    <h1>Count: {{initialState.count}}</h1>
    <h2>New Count: {{newInitialState.value.count }}</h2>
    <h3>Users: {{ newInitialState.user }}</h3>
    <button @click="initialState.count+=1">+1</button> 
    <button @click="initialState.count--">-1</button>

    <button @click="newInitialState.value.count += 10">+ 10</button>
    <button @click="changeUser">Change user</button>
    <button @click="newInitialState.user.push('Gio')">Add new User</button>
</template>

<!-- ref()- used to create reactive reference to a value 
     Unlike reactive functions(above example is of reactive functions)
     which is used for creating reactive objects, ref is specifically designed
     to create reactive single values, ref() is used to make primitive values reactive
     (like numbers, strings, booleans).-->