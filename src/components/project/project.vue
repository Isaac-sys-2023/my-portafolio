<script setup lang="ts">
import { type Tech } from '@/models/tech';

const props = defineProps<{
    title: string
    description: string
    techsUsed: Tech[]
    link: string
    pageLink?: string
    lastUpdate: string
}>()
</script>

<template>
    <div class="project-container">
        <a class="project-title" :href=link>
            {{ title }}
        </a>
        <p v-if="pageLink"><a class="project-page-link" :href=pageLink>{{ pageLink }}</a></p>
        <p>Finish Date: {{ lastUpdate }}</p>
        <p>{{ description }}</p>
        <ul class="techs">
            <li v-for="tech in techsUsed ?? []" :key="tech.name">
                <img class="tech-icon" :src="tech.imageUrl" :alt="tech.name">
            </li>
        </ul>
    </div>
</template>

<style scoped>
.project-container {
    border: 0.2rem solid var(--color-heading);
    border-radius: 1rem;

    margin: 0.5rem;
    padding: 0.5rem;
}

.project-title {
    color: var(--color-heading);
    font-size: 2rem;
    text-align: center;
}

.project-title:hover,
.project-page-link:hover {
    text-decoration: underline;
    background-color: var(--color-bg);
    color: var(--color-heading);
}

.project-page-link {
    background-color: var(--color-heading);
}

.techs {
    list-style: none;
    display: flex;
    justify-content: flex-start;
    padding: 0;
    margin: 0;
}

.tech-icon {
    width: 3rem;
    height: 3rem;
}
</style>
