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
    'toggleNav',
]);

</script>

<template>
    <nav>
        <ul>
            <li v-for="(route, hash) of routes">
                <a :href="hash" :class="{ active: hash == curHash}" @click="$emit('toggleNav')">
                    {{ route.label }}
                </a>
            </li>
        </ul>
    </nav>
</template>

<style scoped>
nav {
    position: fixed;
    bottom: 100%;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    background-color: #565656;
    z-index: 1;
    transition: 0.6s;
}

nav.showing {
    transform: translate(0, 100%);
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
    line-height: 100%;
    width: 100%;
    text-align: center;
    font-size: 32px;
    text-decoration: none;
    color: #C0C0C2;
    padding: 10px;
    transition: 0.4s;
}

a:hover {
    padding: 50px;
    background-color: #373737;
}

.active {
    color: white;
}
</style>