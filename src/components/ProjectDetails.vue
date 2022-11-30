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
const photos = ref(props.project.photos)
const indexPhoto = ref(0)
let backgroundImage = ref(`url("${photos.value[indexPhoto.value]}")`)
function prevPic() {
    if (indexPhoto.value == 0) {
        indexPhoto.value = photos.value.length - 1
    } else {
        indexPhoto.value -= 1
    }
    backgroundImage.value = `url("${photos.value[indexPhoto.value]}")`
}
function nextPic() {
    if (indexPhoto.value == photos.value.length - 1) {
        indexPhoto.value = 0
    } else {
        indexPhoto.value += 1
    }
    backgroundImage.value = `url("${photos.value[indexPhoto.value]}")`
}
</script>

<template>
    <section>
        <div class="background" @click="$emit('suppressDetails')"></div>
        <div class="container">
            <div class="header">
                <div class="picture"></div>
                <div class="prevPic" @click="prevPic()">
                    <div class="bar1"></div>
                    <div class="bar2"></div>
                </div>
                <div class="nextPic" @click="nextPic()">
                    <div class="bar1"></div>
                    <div class="bar2"></div>
                </div>
                <div class="points">
                    <div v-for="photo of photos" class="point" :class="{ 'selectedPoint': (parseInt(photo.split('.')[0].slice(-1)) - 1) == indexPhoto}">
                    </div>
                </div>
            </div>
            <div class="body">
                <div class="title">{{ props.project.title }}</div>
                <div class="description">{{ props.project.description }}</div>
                <div class="links">
                    <a v-if="props.project.link !== ''" :href=props.project.link target="_blank" class="website">VISIT
                        WEBSITE
                        <font-awesome-icon icon="fa-solid fa-globe" />
                    </a>
                    <a v-if="props.project.github !== ''" :href=props.project.github target="_blank"
                        class="github">VISIT
                        GITHUB
                        <font-awesome-icon icon="fab fa-github" />
                    </a>
                </div>
                <div class="exit" @click="$emit('suppressDetails')">
                    <div class="exitContainer">
                        <div class="bar1"></div>
                        <div class="bar2"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.points {
    display: flex;
    gap: 5px;
    justify-content: center;
    margin-top: 5px;
    margin-bottom: 5px;
}

.point {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background-color: #C0C0C2;
    opacity: 50%;
    transition: 0.4s;
}
.selectedPoint{
    opacity: 100%;
    transition: 0.4s;
}
.exit {
    position: fixed;
    left: 100%;
    top: 100%;
    transform: translate(-100%, -100%);
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

.exit .bar1 {
    transform: rotate(-45deg) translate(0, 2px);
    background-color: #A0A1A4;
}

.exit .bar2 {
    transform: rotate(45deg) translate(0, -2px);
    background-color: #A0A1A4;
}

.bar1,
.bar2 {
    width: 19px;
    height: 3px;
    background-color: white;
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
    top: 0;
    transform: translate(0, 0);
    width: 50px;
    height: 60%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 2;
    cursor: pointer;
    background-image: linear-gradient(to left, transparent, #A0A1A4);
}

.nextPic {
    position: fixed;
    left: 100%;
    top: 0;
    transform: translate(-100%, 0);
    width: 50px;
    height: 60%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 2;
    cursor: pointer;
    background-image: linear-gradient(to right, transparent, #A0A1A4);
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
    width: 130px;
    text-align: center;
    padding: 10px 10px 10px 10px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: white;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.4s;
}



.github {
    text-decoration: none;
    width: 130px;
    text-align: center;
    padding: 10px 10px 10px 10px;
    color: #ACBABF;
    font-family: "League Spartan Regular";
    border: 1px solid #ACBABF;
    background-color: white;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.4s;
}


svg {
    margin-left: 5px;
}

@media screen and (min-width: 450px) {
    .github:hover {
        background-color: #ACBABF;
        color: white;
    }

    .website:hover {
        background-color: #ACBABF;
        color: white;
    }
}

@media screen and (max-width: 450px) {
    .container {
        width: 90%;
        height: 80%;
    }

    .title {
        font-size: 16px;
    }

    .description {
        font-size: 14px;
    }

    .body {
        height: 50%;
    }

    .header {
        height: 50%;
    }

    .prevPic {
        height: 50%;
        width: 50px;
    }

    .nextPic {
        height: 50%;
        width: 50px;
    }

    .website {
        font-size: 14px;
        padding: 5px;
        width: 110px;
    }

    .github {
        font-size: 14px;
        padding: 5px;
        width: 110px;
    }

    .links {
        gap: 5px;
    }
}
</style>