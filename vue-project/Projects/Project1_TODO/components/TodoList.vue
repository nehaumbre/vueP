<script setup>
import {ref} from 'vue';

const newTask = ref('');
const tasks = ref([]);

const addTask = () =>{  
    if(newTask.value.trim()!==""){  
        tasks.value.push(newTask.value)
        newTask.value = '';
    }
}

const removeTask = (index) =>{
    tasks.value.splice(index,1);
}
</script>
<template>
    <div class="todo-app">
        <div class="task-input">
            <input v-model= "newTask" @keyup.enter="addTask" placeholder="Add a new task">
            <button @click="addTask">Add to Do</button>
        </div>
    </div>
    <ul class="task-list">
        <li class="task-item" v-for="(task,index) in tasks" :key="index">
            {{ task }}
            <button @click="removeTask(index)" class="remove-button">Remove Task</button>
        </li>
    </ul>
</template>
<style scoped>
.todo-app {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5fff3;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.task-input {
    display: flex;
    gap: 10px;
}

input {
    flex: 1;
    padding: 8px;
    font-size: 14px;
}

button {
    padding: 8px 12px;
    font-size: 14px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

.task-list {
    list-style: none;
    padding: 0;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px 0;
    background-color: #f9f9f9;
    border: 1px solid #b9b0b0;
    border-radius: 9px;
}

.remove-button {
    padding: 6px 10px;
    font-size: 12px;
    background-color: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.remove-button:hover {
    background-color: #c0392b;
}

</style>