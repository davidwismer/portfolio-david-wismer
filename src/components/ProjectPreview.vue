<script setup>
import { ref } from 'vue';
import ProjectDetails from './ProjectDetails.vue';
const props = defineProps({
    project: {
        type: Object,
        require: true
    }
})

//Show the informations on card
const show = ref(false)
const hideImage = ref(false)
function hoverCard() {
    show.value = !show.value
    hideImage.value = !hideImage.value
}

//Make the project details appear
const showDetails = ref(false)
function toggleDetails() {
    showDetails.value = !showDetails.value
}

//Manage the photos of the card
const photo = ref(props.project.photos[0])
const backgroundImage = `url("${photo.value}")`
</script>

<template>
    <section>
        <div class="container" :class="{ 'hideImage': hideImage }" @mouseenter="hoverCard()" @mouseleave="hoverCard()"
            @click="toggleDetails()">
            <div class="text" :class="{ 'show': show }">
                <div class="title">{{ props.project.title }}</div>
                <div class="technologies">
                    <div v-for="technology of props.project.technologies" class="technology">{{ technology }}</div>
                </div>
            </div>
            <div class="more" :class="{ 'show': show }">More</div>
        </div>
        <project-details v-if="showDetails" :project="props.project"
            @suppressDetails="toggleDetails()"></project-details>
    </section>
</template>

<style scoped>
.container {
    transition: 0.3s;
    position: relative;
    width: 300px;
    max-width: 300px;
    height: 300px;
    margin: 20px;
    border-radius: 5px;
    border: 1px solid #ACBABF;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: "League Spartan Regular";
    cursor: pointer;
    justify-content: space-between;
}
.container::before {
    content: "";
    background-image: v-bind(backgroundImage);
    background-size: cover;
    background-position: center;
    position: absolute;
    top: 0px;
    right: 0px;
    bottom: 0px;
    left: 0px;
    border-radius: 5px;
}

.hideImage {
    transition: 0.3s;
    scale: 1.1;
}
.hideImage::before {
    opacity: 0.2;
}

.text {
    position: relative;
    font-size: 18px;
    display: flex;
    opacity: 0;
    flex-direction: column;
    align-items: center;
    margin: 30px;
    color: white;
}

.more {
    position: relative;
    opacity: 0;
    margin-bottom: 30px;
    color: white;
}

.show {
    transition: 0.3s;
    opacity: 1;
}

.title {
    font-family: "League Spartan";
    font-size: 20px;
    margin-bottom: 10px;
    margin-top: 50px;
}

/* On screens that are 450px or less */
@media screen and (max-width: 450px) {
    .text {
        font-size: 14px;
    }

    .title {
        font-size: 16px;
    }
}

.technologies {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    color: #373737;
    gap: 3px 10px;
}

.technology {
    border-radius: 5px;
    padding: 5px 5px 2.5px 5px;
    background-color: #ACBABF;
}
</style>