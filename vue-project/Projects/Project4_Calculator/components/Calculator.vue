<template>
    <div>
        <div class="calculator">
            <input v-model="display" :class="['displayClass', displayClass]" readonly />
            <div class="buttons">
                <button @click="appendToDisplay('7')">7</button>
                <button @click="appendToDisplay('8')">8</button>
                <button @click="appendToDisplay('9')">9</button>
                <button @click="appendToDisplay('/')">/</button>
                <button @click="appendToDisplay('4')">4</button>
                <button @click="appendToDisplay('5')">5</button>
                <button @click="appendToDisplay('6')">6</button>
                <button @click="appendToDisplay('*')">*</button>
                <button @click="appendToDisplay('1')">1</button>
                <button @click="appendToDisplay('2')">2</button>
                <button @click="appendToDisplay('3')">3</button>
                <button @click="appendToDisplay('-')">-</button>
                <button @click="appendToDisplay('0')">0</button>
                <button @click="appendToDisplay('.')">.</button>
                <button @click="calculate()">=</button>
                <button @click="appendToDisplay('+')">+</button>
                <button @click="clearDisplay" class="clear">C</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const display = ref('0')

const appendToDisplay = (value) =>{
    if(display.value === '0' && value !== '.'){  
        display.value = value
    }else{
        display.value += value
    }
}

const calculate = ()=>{
    try{
        display.value = eval(display.value).toString()
    }catch(error){  
        display.value = 'Error'
    }
}

const displayClass = computed(()=>{
    return display.value.length > 12 ? "small-text" : ""
})

const clearDisplay = ()=>{
    display.value = '0'
}
</script>

<style scoped>
/* Container */
.calculator {
    max-width: 320px;
    margin: 40px auto;
    padding: 20px;
    border-radius: 12px;
    background: #1e1e2f;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

/* Display */
.displayClass {
    width: 100%;
    box-sizing: border-box;
    padding: 15px;
    margin-bottom: 15px;
    font-size: 22px;
    text-align: right;
    border: none;
    border-radius: 8px;
    background: #2d2d44;
    color: #fff;
    outline: none;
}

/* Buttons Grid */
.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
}

/* Buttons */
button {
    padding: 15px;
    font-size: 18px;
    border: none;
    border-radius: 8px;
    background: #3a3a5c;
    color: #fff;
    cursor: pointer;
    transition: all 0.2s ease;
}

/* Hover effect */
button:hover {
    background: #50507a;
    transform: translateY(-2px);
}

/* Active (click) effect */
button:active {
    transform: scale(0.95);
}

/* Operator buttons */
button:nth-child(4n) {
    background: #ff9500;
}

button:nth-child(4n):hover {
    background: #e08900;
}

/* Equals button */
button:nth-child(15) {
    background: #28a745;
}

button:nth-child(15):hover {
    background: #218838;
}

/* Clear button */
button.clear {
    grid-column: span 4;
    background: #dc3545;
}

button.clear:hover {
    background: #c82333;
}

.small-text {
    font-size: 16px;
}
</style>
