<template>
  <h1 v-formate-div="100">Using Simple Custom Directive</h1>
   <h1 v-formate-div:orange>Using Simple Custom Directive</h1>
   <h1 v-formate-div:blue>Using Simple Custom Directive</h1>
   <h1 v-formate-div:red>Using Simple Custom Directive</h1>
   <h1 v-formate-div:green>Using Simple Custom Directive</h1>
</template>

<script setup>
const vFormateDiv = {  mounted: (el,binding) =>{
    console.log(el);
    console.log(binding);
    
    let bgColor = 'black';
    let textColor = 'orange';
    let borderColor = 'orange';
    
    switch(binding.arg) {
      case 'red':
        bgColor = '#ff4444';
        textColor = 'white';
        borderColor = 'red';
        break;
      case 'blue':
        bgColor = '#4444ff';
        textColor = 'white';
        borderColor = 'blue';
        break;
      case 'green':
        bgColor = '#44ff44';
        textColor = 'black';
        borderColor = 'green';
        break;
      case 'orange':
      default:
        bgColor = 'black';
        textColor = 'orange';
        borderColor = 'orange';
        break;
    }
    
    el.style.backgroundColor = bgColor;
    el.style.color = textColor;
    el.style.padding = '3rem';
    el.style.fontSize = `${binding.value}px`
    el.style.border = `${binding.value/15}rem solid ${borderColor}`
},}
</script>
