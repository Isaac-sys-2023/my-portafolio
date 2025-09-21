<script setup lang="ts">
import { ref, computed } from "vue";
import { type ContactForm } from "@/models/contactForm";
import FloatingInput from '@/components/floatingInput/floatingInput.vue';

const formData = ref<ContactForm>({
    email: "",
    name: "",
    message: "",
});

const isValidEmail = () => {
    const emailRegex = /^[^@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(formData.value.email);
}

const submitForm = async () => {
    if (!formData.value.name && !formData.value.message && !formData.value.message) {
        //retornar efecto de falla
    }

    if (isValidEmail() === false) {
        //retornar efecto de error
    }



    console.log(`You recieve a message from ${formData.value.name} with the email address ${formData.value.email} and tells you ${formData.value.message} `);
    formData.value = { name: '', email: '', message: '' };
}
</script>

<template>
    <div class="form-container">
        <form class="contact-form" @submit.prevent="submitForm" autocomplete="off">
            <h1>Envia un mensaje</h1>
            <div class="group">
                <!-- <input id="email" type="email" v-model="formData.email" placeholder=" " required>
                <label for="email">Correo Electronico:</label> -->
                <FloatingInput v-model="formData.email" id="email" label="Email" borderColor="purple" />
            </div>
            <div class="group">
                <!-- <input id="name" type="text" v-model="formData.name" placeholder=" " required>
                <label for="name">Nombre:</label> -->
                <FloatingInput v-model="formData.name" id="name" label="Nombre" borderColor="purple" />
            </div>
            <div class="group">
                <!-- <textarea id="message" name="message" rows="5" cols="40" placeholder=" "
                    v-model="formData.message"></textarea> -->
                <!-- <input id="message" type="text" v-model="formData.message" placeholder=" " required> -->
                <!-- <label for="message">Mensaje:</label> -->
                <FloatingInput v-model="formData.message" id="message" label="Mensaje" borderColor="purple"
                    isTextarea />
            </div>
            <div class="form-button">
                <button type="submit">Enviar</button>
            </div>
        </form>
    </div>
</template>

<style>
/* Centrado vertical y horizontal */
.form-container {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;


}

/* Estilo del formulario */
.contact-form {
    width: 100%;
    width: 80%;
    max-width: 400px;
    padding: 2rem;

    background-color: var(--color-bg-hover);
    border-radius: 0.5rem;
    border: 2px solid var(--color-heading);
}

.contact-form h1 {
    text-align: center;
}

.group {
    /* position: relative; */
    margin-bottom: 2rem;

    display: flex;
    flex-direction: column-reverse;
}

/* input,
textarea {
    font-size: 1rem;
    padding: 0.35rem 0.5rem 0.25rem;
    width: 100%;
    border: none;
    border-bottom: 0.0625rem solid var(--color-text);
    outline: none;
    background: transparent;
    color: var(--color-text);
} */

textarea {
    resize: none;
}

/* Estilos de la barra de scroll */
/* Para Chrome, Edge y Safari (WebKit): */
textarea::-webkit-scrollbar {
    width: 0.625rem;
    /* Ancho del scrollbar vertical */
    height: 0.625rem;
    /* Alto del scrollbar horizontal */
}

textarea::-webkit-scrollbar-track {
    background: var(--color-bg-hover);
    /* Color del fondo */
    border-radius: 0.25rem;
}

textarea::-webkit-scrollbar-thumb {
    background-color: var(--color-heading);
    /* Color del "thumb" (la barra que se arrastra) */
    border-radius: 0.25rem;
    border: 2px solid #f0f0f0;
}

textarea::-webkit-scrollbar-thumb:hover {
    background-color: var(--color-bg);
    /* Color al pasar el mouse por encima */
}

/* Para Firefox*/
textarea {
    scrollbar-width: thin;
    /* "auto" | "thin" | "none" */
    scrollbar-color: var(--color-heading) var(--color-bg-hover);
    /* thumb color | track color */
}


/* label {
    font-size: 1rem;
    color: var(--color-text);
    transition: 0.2s ease;
    transform-origin: left top;
    transform: translateY(1.5rem) scale(1);
} */

/* input:placeholder-shown+label,
textarea:placeholder-shown+label {
    font-size: 1rem;
    color: gray;
} */

/* input:focus+label,
input:not(:placeholder-shown)+label,
textarea:focus+label,
textarea:not(:placeholder-shown)+label {
    transform: translateY(0rem) scale(1);
    color: var(--color-text);
}

input:focus,
textarea:focus {
    border-width: 0.125rem;
    border-bottom-color: var(--color-heading);
}

input:focus~label,
textarea:focus~label {
    color: var(--color-heading);
    font-size: 0.75rem;
} */

.form-button {
    display: flex;
    justify-content: center;
    align-items: center;
}

button {
    padding: 0.75rem 1.5rem;
    border: none;
    background-color: var(--color-heading);
    color: var(--color-bg);
    cursor: pointer;
    border-radius: 4px;
    transition: 0.2s ease;
    outline: 0.125rem solid var(--color-heading);
}

button:hover {
    background-color: var(--color-bg-hover);
    color: var(--color-heading);
}
</style>