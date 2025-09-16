<script setup lang="ts">
import { RouterLink } from 'vue-router';
import DarkModeToggle from '../toggle/DarkModeToggle.vue';


</script>

<template>
  <header>
    <h1 class="header-title">Isaac.dev</h1>

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
.header-title {
  color: var(--color-bg);
  width: 3rem;
  overflow: visible;
}

.nav-links {
  list-style: none;
  display: flex;
  justify-content: center;
  padding: 0;
  margin: 0;
}
</style>