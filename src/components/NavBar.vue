<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container">
      <!-- Displayed on larger screens -->
      <ul class="navbar-nav ml-auto d-none d-lg-flex">
        <li class="nav-item">
          <router-link class="nav-link" :to="{ path: '/careermap' }" :class="{ 'active': isActive('/careermap') }">Career Map</router-link>
        </li>
        <li class="nav-item">
          <span v-if="!isSkillsMapClickable" class="nav-link inactive-link">Skills Map</span>
          <router-link v-else class="nav-link" :to="{ path: '/skillsmapmain' }" :class="{ 'active': isActive('/skillsmapmain') }">Skills Map</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" :to="{ path: '/functionalskills' }" :class="{ 'active': isActive('/functionalskills') }">Functional Skills</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" :to="{ path: '/enablingskills' }" :class="{ 'active': isActive('/enablingskills') }">Enabling Skills</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" :to="{ path: '/abouthePSF' }" :class="{ 'active': isActive('/about') }">About</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" :to="{ path: '/contactus' }" :class="{ 'active': isActive('/contactus') }">Contact Us</router-link>
        </li>
      </ul>

      <!-- Displayed on smaller screens -->
      <div class="d-lg-none">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" :to="{ path: '/careermap' }" :class="{ 'active': isActive('/careermap') }">Career Map</router-link>
          </li>
          <li class="nav-item">
            <span v-if="!isSkillsMapClickable" class="nav-link inactive-link">Skills Map</span>
            <router-link v-else class="nav-link" :to="{ path: '/skillsmapmain' }" :class="{ 'active': isActive('/skillsmapmain') }">Skills Map</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{ path: '/functionalskills' }" :class="{ 'active': isActive('/functionalskills') }">Functional Skills</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{ path: '/enablingskills' }" :class="{ 'active': isActive('/enablingskills') }">Enabling Skills</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{ path: '/abouthePSF' }" :class="{ 'active': isActive('/about') }">About</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{ path: '/contactus' }" :class="{ 'active': isActive('/contactus') }">Contact Us</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { defineProps, ref, onMounted, watch } from 'vue';
import { RouterLink, useRoute } from 'vue-router';

const props = defineProps(['to']);
const route = useRoute();
const activeLink = ref('');
const isSkillsMapClickable = true;

const isActive = (path) => {
  return route.path === path;
};

onMounted(() => {
  // Set the active link initially on component mount
  setActiveLink();
});

// Watch for route changes and update the active link
watch(() => route.path, () => {
  setActiveLink();
});

const setActiveLink = () => {
  activeLink.value = route.path;
};
</script>

<style scoped>
.nav-item {
  margin-left: 50px;
  margin-right: 50px;
}

.nav-link {
  text-align: center !important;
}

.navbar-nav .nav-item .active {
  color: #007bff;
  /* Change to your desired active link color */
  text-decoration: underline;
  /* Add underline to the active link */
}

/* Add any component-specific styles here */
</style>
