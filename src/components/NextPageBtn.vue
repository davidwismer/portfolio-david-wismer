<script setup>
import { ref } from 'vue';
const props = defineProps({
    curHash: {
        type: String,
        required: true
    }
});

function nextPage() {
    let nextHash = "#portfolio"
    if (props.curHash == "#portfolio") nextHash = "#contact"
    location.hash = nextHash
}
</script>

<template>
    <div class="container" @click="nextPage()">
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
    width: 5%;
    height: 60%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    z-index: 2;
    cursor: pointer;
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
</style>