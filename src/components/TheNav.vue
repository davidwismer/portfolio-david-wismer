<script setup>
const props = defineProps({
    routes: {
        type: Object,
        required: true
    },
    curHash: {
        type: String,
        required: true
    }
});

const emit = defineEmits([
    'toggleNav'
]);
</script>

<template>
    <nav>
        <ul>
            <li v-for="(route, hash) of routes">
                <a :href="hash" :class="{ active: hash == curHash }" @click="$emit('toggleNav')">
                    {{ route.label }}
                </a>
            </li>
        </ul>
    </nav>
</template>

<style scoped>
nav {
    position: fixed;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    background-color: #828385;
    z-index: 1;
}

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

li {
    height: 150px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

a {
    width: 100%;
    height: 100%;
    text-align: center;
    font-size: 32px;
    text-decoration: none;
    color: #C0C0C2;
}
a:hover {
    background-color: #565656;
}

.active {
    color: white;
}
</style>