<script setup>
import { ref } from 'vue';
const props = defineProps({
    curHash: {
        type: String,
        required: true
    }
});

function nextPage() {
    let nextHash = "#projects"
    if (props.curHash == "#projects") nextHash = "#contact"
    location.hash = nextHash
}
//Hover effect on button
const hover = ref(false)
function hoverEffect() {
    hover.value = !hover.value
}
</script>

<template>
    <div class="container" :class="{'hoverEffect': hover}" @mouseenter="hoverEffect()" @mouseleave="hoverEffect()" @click="nextPage()">
        <div class="bar1"></div>
        <div class="bar2"></div>
    </div>
</template>

<style scoped>
.container {
    position: fixed;
    left: 100%;
    top: 50%;
    transform: translate(-100%, -50%);
    width: 50px;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    z-index: 2;
    cursor: pointer;
    transition: 0.4s;
}
.hoverEffect{
    background: linear-gradient(to right, transparent, #303030);
    width: 75px;
}
.bar1,
.bar2 {
    width: 35px;
    height: 3px;
    background-color: #828385;
}

.bar1 {
    transform: rotate(45deg) translate(0, -14px);
}

.bar2 {
    transform: rotate(-45deg) translate(0, 14px);
}

@media screen and (max-width: 450px) {
    .container{
        display: none;
    }
}
</style>