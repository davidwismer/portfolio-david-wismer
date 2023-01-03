<script setup>
import { ref, toRef, watch } from 'vue';
//Get the boolean if the nav is active or not in the app.vue
const props = defineProps({
    change: {
        type: Boolean,
        required: true
    }
});
//Makes that i can modify 'change' without getting a read-only error
const change = ref('');
const changeRo = toRef(props, 'change');
watch(changeRo, (value) => {
    change.value = changeRo.value;
});

function toggleButton() {
    change.value = !change.value
}
</script>

<template>
    <div :class="{
        'container': true,
        'change': change
    }" @click="toggleButton()">
        <div class="bar1"></div>
        <div class="bar2"></div>
        <div class="bar3"></div>
    </div>
</template>

<style scoped>
.container {
    position: fixed;
    left: 100%;
    top: 0%;
    margin-top: 50px;
    margin-left: -110px;
    display: inline-block;
    cursor: pointer;
    z-index: 3;
    transition: 0.4s;
}

.container:hover {
    scale: 1.2;
    transition: 0.4s;
}

.bar1,
.bar2,
.bar3 {
    width: 35px;
    height: 3px;
    background-color: #828385;
    margin: 6px 0;
    transition: 0.6s;
}

.change .bar1 {
    transform: translate(0, 9px) rotate(-45deg);
}

.change .bar2 {
    opacity: 0;
}

.change .bar3 {
    transform: translate(0, -9px) rotate(45deg);
}

@media screen and (max-width: 450px) {
    .container{
        margin-top: 20px;
        margin-left: -60px;
    }
}
</style>