<script setup>
defineProps({ friends :Array, userinfo: Object })

</script>
<template>
    <h1>Complex Props</h1>
    <h1>{{ friends }}</h1>
    <h1>{{ userinfo }}</h1>
    <ul v-for="(friend, index) in friends" :key="index">
        <li>{{ friend }}</li>
    </ul>
    <ul v-for="(info,k, index) in userinfo" :key="index">
        <li>{{k}}:{{ info }}</li>
    </ul>
</template>