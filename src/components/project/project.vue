<script setup lang="ts">
import { type Tech } from '@/models/tech';

const props = defineProps<{
    title: string
    description: string
    techsUsed: Tech[]
    link: string
    pageLink?: string
    lastUpdate: string
    types: string[]
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
        <div class="project-types">
            <h3 class="project-type" v-for="type in types ?? []" :key="type">{{ type }}</h3>
        </div>
    </div>
</template>

<style scoped>
.project-container {
    outline: 0.2rem solid var(--color-heading);
    border-radius: 1rem;

    margin: 0.5rem;
    padding: 0.5rem;

    transition: all 0.2s ease;
}

.project-container:hover {
    outline: 0.4rem solid var(--color-heading)
}

.project-title {
    color: var(--color-heading);
    font-size: 2rem;
    text-align: center;
}

.project-title:hover,
.project-page-link:hover {
    text-decoration: underline;
    color: var(--color-heading);
}

.project-title:hover,
.project-page-link:hover,
.project-container:hover {
    background-color: var(--color-bg-hover);
}

.project-page-link {
    background-color: var(--color-heading);
}

.techs {
    list-style: none;
    display: flex;
    justify-content: flex-start;
    padding: 0;
    margin: 0.5rem 0;
    gap: 0.5rem;
}

.tech-icon {
    width: 3rem;
    height: 3rem;

    transition: transform 0.3s ease;
}

.tech-icon:hover {
    transform: scale(1.25);
}

.project-types {
    display: flex;
    flex-direction: row;
}

.project-type {
    background-color: var(--color-heading);
    color: var(--color-bg);
    border-radius: 0.5rem;
    padding: 0.5rem;
    margin-right: 0.25rem;

    overflow: hidden;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s, box-shadow 0.3s;

}

.project-type:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}
</style>
