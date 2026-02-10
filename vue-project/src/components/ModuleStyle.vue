
<template>
    <!-- <h1 v-bind:class="$style['m-class']">Using Module CSS with $ syntax (kabab-case)</h1> -->
    <!-- <h1 :class="$style['m-class']">Using Module CSS with $ syntax (kabab-case)</h1>
    <h2 :class="$style.anotherClass">Using Module CSS with $ syntax (Camel-case)</h2> -->
    <h1 :class="myClasses['m-class']">Using Module CSS with $ syntax (kabab-case)</h1>
    <h2 :class="myClasses.anotherClass">Using Module CSS with $ syntax (Camel-case)</h2>
</template>

<style module="myClasses">
.m-class {
    color: rgb(252, 255, 250);
    background-color: rgb(81, 101, 166);
}

.anotherClass {
    background: peachpuff;
    color: darkblue;
}
</style>