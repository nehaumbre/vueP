<script setup>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

const message = ref("Lets learn about vue lifecycle hooks")

//Lifecycle Hooks
onBeforeMount(()=>{  
  console.log('Component is about to be mounted');
})

onMounted(()=>{ console.log('component has been mounted')})

//to update the message when button is clicked
const updateMessage = ()=> { message.value = "Message has been updated!"}

onBeforeUpdate(()=>{ console.log('component is about to be updated')})
onUpdated(()=>{ console.log('component has been updated')})

onBeforeUnmount(()=>{ console.log('component is about to be unmounted')})
onUnmounted(()=>{ console.log('component has been unmounted')})
</script>
<template>
  <p>{{ message }}</p>
  <button @click="updateMessage">Update Message</button>
</template>
