<script setup lang="ts">
import { ref } from 'vue';
import Project from '@/components/project/project.vue';

import cssLogo from '@/assets/tech/CSS3.svg';
import htmlLogo from '@/assets/tech/html.svg';
import jsLogo from '@/assets/tech/JavaScript.svg';
import tsLogo from '@/assets/tech/typescript.svg';
import nestLogo from '@/assets/tech/nestjs-icon.svg';
import cloudinaryLogo from '@/assets/tech/cloudinary.svg';
import renderLogo from '@/assets/tech/render.svg';
import swaggerLogo from '@/assets/tech/Swagger.svg';

const myProjects = ref([
    {
        title: "Js Gym Practice",
        description: "Esta es una pagina web hecha para un gym",
        techsUsed: [
            { imageUrl: cssLogo, name: "CSS 3" },
            { imageUrl: htmlLogo, name: "HTML 5" },
            { imageUrl: jsLogo, name: "JS" }
        ],
        link: "https://github.com/Isaac-sys-2023/JS_Gym_Practice.git",
        lastUpdate: "30 Sep 2024",
        types: ["Frontend"],
    },
    {
        title: "Scesi Ecommerce",
        description: "Este es un backend hecho para usarlo como una forma de enseñar React con TS en la SCESI",
        techsUsed: [
            { imageUrl: nestLogo, name: "Nest JS" },
            { imageUrl: tsLogo, name: "TS" },
            { imageUrl: swaggerLogo, name: "Swagger" },
            { imageUrl: cloudinaryLogo, name: "Cloudinary" },
            { imageUrl: renderLogo, name: "Render" }
        ],
        link: "https://github.com/Isaac-sys-2023/scesi-ecommerce-api.git",
        lastUpdate: "30 Sep 2024",
        types: ["Backend"],
    }
]);

const actualParam = ref("all");

let filteredProject = ref(myProjects.value);

const filterProject = (paramFilter: string) => {
    actualParam.value = paramFilter;

    if (paramFilter === 'all' || paramFilter === '') {
        filteredProject.value = myProjects.value;
        return;
    }
    filteredProject.value = myProjects.value.filter(f => f.types.includes(paramFilter));
}

</script>

<template>
    <div class="projects-items-container">
        <h1>My proyects</h1>
        <div class="filter-buttons">
            <button :class="['filter-button', { selected: actualParam === 'all' }]" @click="filterProject('all')">All
                ({{ myProjects.length }})</button>
            <button :class="['filter-button', { selected: actualParam === 'Frontend' }]"
                @click="filterProject('Frontend')">Frontend ({{myProjects.filter(f =>
                    f.types.includes('Frontend')).length}})</button>
            <button :class="['filter-button', { selected: actualParam === 'Backend' }]"
                @click="filterProject('Backend')">Backend ({{myProjects.filter(f => f.types.includes('Backend')).length
                }})</button>
            <button :class="['filter-button', { selected: actualParam === 'Mobile' }]"
                @click="filterProject('Mobile')">Mobile ({{myProjects.filter(f => f.types.includes('Mobile')).length
                }})</button>

        </div>
        <div class="projects-items" v-if="filteredProject.length > 0">
            <Project class="project-item" v-for="project in filteredProject" :key="project.title" v-bind="project" />
        </div>
        <p v-else>No hay proyectos disponibles</p>
    </div>
</template>

<style>
.projects-items-container {
    padding: 1rem;
}

.projects-items {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.projects-items,
.project-item {
    width: 100%;
    /* o max-width, si quieres limitarlo */
}

.filter-buttons {
    width: 100%;
    display: flex;
    justify-content: center;
}

.filter-button {
    width: 7rem;
    padding: 0.5rem;
    margin: 0.5rem;
    /* border: 0.2rem solid var(--color-heading); */
    outline: 0.15rem solid var(--color-heading);
    border-radius: 0.45rem;
    background-color: var(--color-heading);

    transition: all 0.3s ease;
    color: var(--color-bg);
    font-size: 1rem;
}

.filter-button:hover,
.filter-button.selected {
    transform: scale(1.05);
    background-color: var(--color-bg);
    color: var(--color-text);
}
</style>
