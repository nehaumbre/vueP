<script setup>
const props = defineProps(['firstname','lastname','myFavoriteNumber'])
// props.myFavoriteNumber = 6 ❌
//cannot change value of prop as it is 7 (target is readonly)
// props.firstname ='kim'❌
//cannot change value of prop as it is John (target is readonly)
//hence props are immutable
</script>
<template>
    <h1>Dynamic PROPS</h1>
    <h2>{{props.firstname }} {{ props.lastname }}</h2>
    <h1>{{props.myFavoriteNumber}}</h1>
</template>