<!-- Conditional rendering
    means showing or hiding elements in your webpage 
    based on a condition (like true/false). 
    In Vue, you mainly use:
    v-if
    v-else
    v-else-if
    v-show-->
   
<script setup>
import { ref } from 'vue';
// const isTrue = false
// const isFalse = true

const isVisible = ref(true)
const isActive = ref(true)
let passCode = ref('12345678')

// const isUserLoggedIn = ref(true)
// const username = "admin"
// const showDetails = ref(isUserLoggedIn)
</script>
<template>
    <!-- <h1>Hello</h1>
    <div>
        <p v-if="isTrue">This will show if isTrue is true</p>
        <p v-else-if="isFalse">This will show if isFalse is true</p>
        <p v-else>This will show if both isTrue and isFalse are false</p>
    </div> -->
    <div>
        <p v-show="isVisible">Lorem ipsum dolor sit amet consectetur adipisicing</p>
        <button @click="isVisible = !isVisible">Toggle isVisible</button>
    </div>
    <!-- <div>
        <h1 v-if="isUserLoggedIn">Welcome , {{username}}</h1>
        <h1 v-else>Please login to access dashboard</h1>
        <div>
            <p v-show="showDetails">You can now access the dashboard</p>
        </div>
    </div> -->
    <div v-if="isActive">
        <h1>My Blog Post</h1>
        <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Atque maxime temporibus autem doloremque numquam facilis odit animi, excepturi suscipit recusandae, dicta facere fuga. Doloremque vel ipsa expedita, magni consequatur id.</p>
    </div>
    <button @click="isActive = !isActive">Toggle Post</button>
    <div>
        <h1 v-if="passCode.length > 8">Passcode is valid</h1>
        <h1 v-else-if="passCode.length <8 && passCode.length> 0 ">Passcode is invalid</h1>
        <h1 v-else>Please Enter Password</h1>
    </div>
</template>