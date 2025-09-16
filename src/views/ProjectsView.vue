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
</script>

<template>
    <div class="projects">
        <h1>My proyects ({{ myProjects.length }}):</h1>
        <div>
            <Project v-for="project in myProjects" v-bind="project" />
        </div>
    </div>
</template>

<style></style>
