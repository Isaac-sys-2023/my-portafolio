<script setup>
import { ref } from "vue";

const formData = ref({
    email: "",
    name: "",
    message: "",
});
</script>

<template>
    <div class="form-container">
        <form class="contact-form" @submit.prevent>
            <h1>Envia un mensaje</h1>
            <div class="group">
                <input id="email" type="email" v-model="formData.email" placeholder=" " required>
                <label for="email">Correo Electronico:</label>
            </div>
            <div class="group">
                <input id="name" type="text" v-model="formData.name" placeholder=" " required>
                <label for="name">Nombre:</label>
            </div>
            <div class="group">
                <input id="message" type="text" v-model="formData.message" placeholder=" " required>
                <label for="message">Mensaje:</label>
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
    min-height: 70vh;
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

input {
    font-size: 1rem;
    padding: 0.35rem 0.5rem 0.25rem;
    width: 100%;
    border: none;
    border-bottom: 0.0625rem solid var(--color-text);
    outline: none;
    background: transparent;
    color: var(--color-text);
}

label {
    font-size: 1rem;
    color: var(--color-text);
    transition: 0.2s ease;
    transform-origin: left top;
    transform: translateY(1.5rem) scale(1);
}

input:placeholder-shown+label {
    font-size: 1rem;
    color: gray;
}

input:focus+label,
input:not(:placeholder-shown)+label {
    transform: translateY(0rem) scale(1);
    color: var(--color-text);
}

input:focus {
    border-width: 0.125rem;
    border-bottom-color: var(--color-heading);
}

input:focus~label {
    color: var(--color-heading);
}

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
}

button:hover {
    background-color: var(--color-secondary);
    color: var(--color-text);
}
</style>