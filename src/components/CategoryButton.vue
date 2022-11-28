<script setup>
const emit = defineEmits([
    'toggleCategory',
]);
</script>

<template>
    <div @click="$emit('toggleCategory')">
        <slot></slot>
    </div>
</template>

<style scoped>
.category {
    padding: 10px 10px 7px 10px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: #373737;
    border-radius: 5px;
    cursor: pointer;
}

.selected {
    color: #373737;
    background-color: #ACBABF;
    border: 1px solid #373737;
}
</style>