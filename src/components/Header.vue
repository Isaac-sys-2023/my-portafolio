<script setup lang="ts">
import { RouterLink } from 'vue-router';
import DarkModeToggle from './DarkModeToggle.vue';


</script>

<template>
  <header>
    <ul class="nav-links">
      <li>
        <RouterLink to="/">Home</RouterLink>
      </li>
      <li>
        <RouterLink to="/about">About</RouterLink>
      </li>
      <li>
        <RouterLink to="/projects">Projects</RouterLink>
      </li>
    </ul>

    <DarkModeToggle />
  </header>
</template>

<style scoped>
.nav-links {
  list-style: none;
  display: flex;
  justify-content: center;
  gap: 2rem;
  padding: 0;
  margin: 0;
}
</style>