<script setup>
import { ref } from 'vue';

const props = defineProps({
    project: {
        type: Object,
        required: true
    }
})

const emit = defineEmits([
    'suppressDetails',
]);

//Manage the photos of the card
const photo = ref(props.project.photos[0])
const backgroundImage = `url("${photo.value}")`
</script>

<template>
    <section>
        <div class="background" @click="$emit('suppressDetails')"></div>
        <div class="container">
            <div class="header">
                <div class="picture"></div>
                <div class="prevPic">
                    <div class="bar1"></div>
                    <div class="bar2"></div>
                </div>
                <div class="nextPic">
                    <div class="bar1"></div>
                    <div class="bar2"></div>
                </div>
            </div>
            <div class="body">
                <div class="title">{{ props.project.title }}</div>
                <div class="description">{{ props.project.description }}</div>
                <div class="links">
                    <a v-if="props.project.link !== ''" :href=props.project.link target="_blank" class="website">VISIT
                        WEBSITE</a>
                    <a v-if="props.project.github !== ''" :href=props.project.github target="_blank" class="github">VIEW
                        GITHUB</a>
                </div>

            </div>
        </div>
    </section>
</template>

<style scoped>
.bar1,
.bar2 {
    width: 19px;
    height: 3px;
    background-color: #828385;
}

.prevPic .bar1 {
    transform: rotate(-45deg) translate(0, -6px);
}

.prevPic .bar2 {
    transform: rotate(45deg) translate(0, 6px);
}

.nextPic .bar1 {
    transform: rotate(45deg) translate(0, -6px);
}

.nextPic .bar2 {
    transform: rotate(-45deg) translate(0, 6px);
}

.prevPic {
    position: fixed;
    left: 0%;
    top: 50%;
    transform: translate(0, -50%);
    width: 5%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-end;
    z-index: 2;
    cursor: pointer;
}

.nextPic {
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

.background {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: #565656;
    opacity: 0.75;
    z-index: 10;
}

.container {
    position: fixed;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -40%);
    width: 50%;
    height: 75%;
    background-color: white;
    z-index: 11;
    display: flex;
    flex-direction: column;
}

.header {
    width: 100%;
    height: 60%;
}

.picture {
    width: 100%;
    height: 100%;
    background-image: v-bind(backgroundImage);
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
}

.body {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 40%;
    font-family: "League Spartan Regular";
}

.title {
    font-family: "League Spartan";
    font-size: 20px;
    height: 20%;
    margin-left: 20px;
    margin-right: 20px;
    margin-top: 20px;
    color: #A0A1A4;
}

.description {
    height: 60%;
    margin-left: 20px;
    margin-right: 20px;
    color: #A0A1A4;
}

.links {
    height: 20%;
    margin-left: 20px;
    margin-right: 20px;
    margin-bottom: 20px;
    display: flex;
    gap: 20px;
    align-items: flex-end;
}

.website {
    text-decoration: none;
    width: 100px;
    text-align: center;
    padding: 10px 10px 7px 10px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: white;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.4s;
}

.website:hover {
    background-color: #ACBABF;
    color: white;
}

.github {
    text-decoration: none;
    width: 100px;
    text-align: center;
    padding: 10px 10px 7px 10px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: white;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.4s;
}

.github:hover {
    background-color: #ACBABF;
    color: white;
}
</style>