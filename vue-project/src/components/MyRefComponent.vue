<script setup>
import { reactive,ref } from 'vue';

let count  = ref(0)
let username = ref('')
let userList = ref(["Gin","Shinpachi"])
let friends = reactive([ref('Kiaus'), ref('Alex'), ref('Zoro')])


const profile = ref({
  name: 'Sakata Gintoki',
  age: 27,
  isSamurai: true,
  skills: ['Swordsmanship', 'Wooden Sword Fighting'],
  address: {
    city: 'Edo',
    country: 'Japan'
  }
})

const toggleSamurai = () => {
  profile.value.isSamurai = !profile.value.isSamurai
}
</script>

<template>
    <h1>Count: {{ count }}</h1>
    <h2>Username : {{username }}</h2>
    <h3>Gintama Trio :{{ userList }} </h3>
    <button @click="count++">increment</button>
    <button @click="count--">decrement</button>
    <button @click="username ='jordan'">add user</button>
    <button @click="userList.push('kagura')">add trio character</button>
    <p>Gintama profile : 
        name: {{ profile.name }} <br>
        age:  {{ profile.age }} <br>
        isSamurai: {{ profile.isSamurai }} <br>
        skills: {{ profile.skills }} <br>
        address:{{ profile.address }}
    </p>
    <button @click="profile.name = 'Gin chan'">Change name</button>
    <button @click="profile.age++">Increase age by 1</button>
    <button @click="toggleSamurai">Toggle : is samurai?</button>
    <button @click="profile.skills.push('Comedy')">Add new skill</button>
    <button @click="profile.address.city='edo'">Change city inside address</button>
    <h1>Friends: {{ friends[0] }}</h1>
    <h1>Friends: {{ friends[1] }}</h1>
    <h1>Friends: {{ friends[2] }}</h1>
    <button @click="friends[0]='🤝'">handshake</button>
    <button @click="friends[1]='🤝'">handshake</button>
    <button @click="friends[2]='🤝'">handshake</button>
</template>