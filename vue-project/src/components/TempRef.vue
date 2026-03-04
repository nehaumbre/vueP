<script setup>
import { ref, onMounted } from "vue";
const myRef = ref("hi");
// const myRef = ref('hi')
// console.log(myRef.value); //gives value of the ref 'hi'

onMounted(() => {
  console.log(myRef.value);
  myRef.value.focus(); //focuses the input element when the component is mounted
  myRef.value.value = "welcome to template ref"; //sets the value of the input element to 'welcome to template ref'
}); //reference to the DOM element will be available

// =======================================
const myRefFunc = (element) => {
  console.log(element.textContent);
  element.textContent = "Text changed using template ref function!";
  element.style.color = "cyan"
};
</script>
<template>
  <h1>Template Ref</h1>
  <input type="text" ref="myRef" placeholder="Enter something..." />
  <hr />
  <hr>
  <p :ref="myRefFunc">
    it is a way to create a reference to a child component element or a DOM
    element within a template which allows you to access and manipulate the
    referenced object directly in your components logic
  </p>
</template>
