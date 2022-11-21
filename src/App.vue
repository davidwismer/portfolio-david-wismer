<script setup>
import { ref, computed } from 'vue'
import AppAbout from './AppAbout.vue'
import AppPortfolio from './AppPortfolio.vue'
import AppContact from './AppContact.vue'
import TheNav from './components/TheNav.vue'
import TheNavButton from './components/TheNavButton.vue'
import PreviousPageBtn from './components/PreviousPageBtn.vue'
import NextPageBtn from './components/NextPageBtn.vue'

//construction des routes
const routes = {
  "#about": {
    label: "About",
    id: "about",
    component: AppAbout,
  },
  "#portfolio": {
    label: "Portfolio",
    id: "portfolio",
    component: AppPortfolio,
  },
  "#contact": {
    label: "Contact",
    id: "contact",
    component: AppContact,
  }
};

//Get current Hash
const hash = ref(window.location.hash);
window.addEventListener('hashchange', () => hash.value = window.location.hash);
const curHash = computed(() => routes[hash.value] ? hash.value : Object.keys(routes)[0]);

//Manage nav menu
const isNavActive = ref(false)
function toggleNav() {
  isNavActive.value = !isNavActive.value
}

</script>

<template>
  <the-nav-button :change="isNavActive" @click="toggleNav()"></the-nav-button>
  <previous-page-btn v-if="curHash == '#portfolio' || curHash == '#contact'" :curHash="curHash"></previous-page-btn>
  <next-page-btn v-if="curHash == '#about' || curHash == '#portfolio'" :curHash="curHash"></next-page-btn>
  <the-nav :routes="routes" :curHash="curHash"
    :class="{ 'showing': isNavActive }"
    @toggleNav="toggleNav()"></the-nav>

  <main>
    <template v-for="(route, hash) of routes">
      <div v-show="hash == curHash">
        <component :is="route.component" />
      </div>
    </template>
  </main>

</template>

<style>
@font-face {
  font-family: "League Spartan";
  src: local("League Spartan"),
    url(./fonts/LeagueSpartan-Bold.otf) format("truetype");
}

@font-face {
  font-family: "League Spartan Regular";
  src: local("League Spartan Regular"),
    url(./fonts/LeagueSpartan-Regular.otf) format("truetype");
}

html {
  font-family: "League Spartan";
  margin: 0;
  padding: 0;
}

html::-webkit-scrollbar {
  display: none;
}

body {
  padding: 0;
  margin: 0;
  color: #C0C0C2;
  background-color: #373737;
}
</style>
