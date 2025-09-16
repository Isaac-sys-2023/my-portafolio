<script setup lang="ts">
import { ref } from 'vue';
import TheWelcome from '../components/TheWelcome.vue'
import project from '../components/project/project.vue';
import { type Tech } from '@/models/tech';

import cssLogo from '@/assets/tech/CSS3.svg';
import htmlLogo from '@/assets/tech/html.svg';
import jsLogo from '@/assets/tech/JavaScript.svg';
import tsLogo from '@/assets/tech/typescript.svg';
import nestLogo from '@/assets/tech/nestjs-icon.svg';
import cloudinaryLogo from '@/assets/tech/cloudinary.svg';
import renderLogo from '@/assets/tech/render.svg';
import swaggerLogo from '@/assets/tech/Swagger.svg';

const today = new Date();
const myBirthday = new Date('2004/06/21 20:31:00');
const myAge = today.getFullYear() - myBirthday.getFullYear();

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
    types: ["Backend", "Frontend"],
  }
]);
</script>

<template>
  <!-- <main>
    <TheWelcome />
  </main> -->
  <div class="home-container">
    <img class="me" src="../assets/isaac.jpeg" alt="Isaac" draggable="false">
    <p>
      Hola, soy Isaac, soy un desarrollador web y móvil de {{ myAge }} años de edad.
      Bienvenido a mi portafolio :D
    </p>
  </div>

  <div>
    <h2>Some of my projects:</h2>
    <project v-for="project in myProjects" v-bind="project" />
  </div>
</template>

<style scoped>
.home-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  gap: 1rem;
}

.me {
  height: 8rem;
  width: 8rem;
  border-radius: 50%;

  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  pointer-events: none;
}
</style>
