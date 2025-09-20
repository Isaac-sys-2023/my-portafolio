<script setup lang="ts">
import { RouterLink } from 'vue-router';
import DarkModeToggle from '../toggle/DarkModeToggle.vue';


</script>

<template>
  <header>
    <div class="left">
      <h1 class="header-title">Isaac.dev</h1>
    </div>

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
      <li>
        <RouterLink to="/contact">Contact</RouterLink>
      </li>
    </ul>

    <div class="right">
      <DarkModeToggle />
    </div>
  </header>
</template>

<style scoped>
.header-title {
  color: var(--color-bg);
  width: 3rem;
  overflow: visible;
  font-weight: bold;
}

.nav-links {
  list-style: none;
  display: flex;
  justify-content: center;
  padding: 0;
  margin: 0;
  gap: 1rem;
}
</style>