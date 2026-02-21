<script setup>
import { inject } from 'vue';
const friendsList = inject('friends')
const games = inject('games')
const moreGames = inject('moreGames')
</script>
<template>
    <!-- <h1>Practise</h1> -->
    <h4>Injecting Array</h4>
    <ul v-for="(friend, index) in friendsList" :key="index"><li>{{ friend }}</li></ul>
    <h4>Injecting Object</h4>
    <ul v-for="(game, index) in games" :key="index"><li>{{ game }}</li></ul>
    <h4>Array of Objects</h4>
    <ul v-for="(moreGame, index) in moreGames" :key="index">
        <li>{{ moreGame }}</li>
    </ul>
    <h4>Array of Objects Destructuring</h4>
    <ul v-for="({title,genre, platform , releaseDate }, index) in moreGames" :key="index">
        <li>{{ title }}</li>
        <li>{{ platform }}</li>
        <li>{{ releaseDate }}</li>
        <li>{{ genre }}</li>
    </ul>
</template>