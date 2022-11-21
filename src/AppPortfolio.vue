<script setup>
import { ref } from 'vue';
import portfolio from "./data/portfolio.json"
import CategoryButton from './components/CategoryButton.vue';
import ProjectPreview from './components/ProjectPreview.vue'

//Manage the current category selected
const categories = portfolio[0].categories
const curSelected = ref('all')
function toggleCategory() {
    curSelected.value = event.target.classList[1]
}

//Manage the projects
const projects = portfolio[0].projects
//show project if one of the categories of it is the same as filter
function showProject(category){
    return category == curSelected.value
}
</script>

<template>
    <section class="portfolio-content">
        <div class="header">
            <div class="title">My projects</div>
            <div class="categories">
                <category-button v-for="category of categories" class="category"
                    :class="[category.split(' ')[0].toLowerCase(), { 'selected': curSelected == category.split(' ')[0].toLowerCase() }]"
                    @toggleCategory="toggleCategory()">{{ category.toUpperCase() }}</category-button>
            </div>
        </div>
        <div class="projects">
            <project-preview v-for="project of projects" class="project-preview" :project="project" v-show="project.category.some(showProject) || curSelected == 'all'"></project-preview>
        </div>
    </section>
</template>

<style scoped>
section {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.header {
    margin-top: 100px;
    width: 80%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.projects {
    width: 80%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
}

.categories {
    width: 75%;
    display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap;
    gap: 15px;
}

.title {
    font-size: 32px;
    margin-bottom: 30px;
}
</style>