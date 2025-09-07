<template>
    <div class="mode-toggle">
        <input type="checkbox" id="darkmode-toggle" />
        <label class="darkmode-toggle" for="darkmode-toggle">
            <!-- <img class="sun" src="../assets/sun.gif" /> -->
            <sun class="sun" />
            <img class="moon" src="../assets/night.gif" />
        </label>
    </div>
</template>

<script lang="ts">
import sun from './icons/themeToggleIcons/sun.vue';
export default {
    components: { sun },
    data() {
        return {};
    },
    mounted() {
        // identify the toggle switch HTML element
        const toggleSwitch = document.querySelector<HTMLInputElement>('input#darkmode-toggle[type="checkbox"]');

        // listener for changing themes
        toggleSwitch!.addEventListener('change', this.switchTheme, false);

        // get the localStorage theme value if it exists set the theme to the value
        const currentTheme = localStorage.getItem('theme') ? localStorage.getItem('theme') : null;
        currentTheme && document.documentElement.setAttribute('data-theme', currentTheme);

        // pre-check the dark-theme checkbox if dark-theme is set
        if (document.documentElement.getAttribute("data-theme") == "dark") {
            toggleSwitch!.checked = true;
        }
    },

    methods: {
        // function that changes the theme, and sets a localStorage variable to track the theme between page loads
        switchTheme(e: Event) {
            const toggleSwitch = document.querySelector<HTMLInputElement>('input#darkmode-toggle[type="checkbox"]');
            if ((<HTMLInputElement>e.target).checked) {
                localStorage.setItem('theme', 'dark');
                document.documentElement.setAttribute('data-theme', 'dark');
                toggleSwitch!.checked = true;
            } else {
                localStorage.setItem('theme', 'light');
                document.documentElement.setAttribute('data-theme', 'light');
                toggleSwitch!.checked = false;
            }
        },
    },
};
</script>

<style scoped>
img,
.sun {
    height: 3rem;
    width: 3rem;

    transition: 0.4s;
    padding: 5px;

    border-radius: 0.5rem;
}

img:hover,
.sun:hover {
    background-color: var(--color-accent);
}

.darkmode-toggle {
    display: flex;
    justify-content: center;
    align-items: center;
}

/* Mostrar solo el sol en light mode */
:root[data-theme="light"] .moon {
    display: none;
}

:root[data-theme="light"] .sun {
    display: block;
}

/* Mostrar solo la luna en dark mode */
:root[data-theme="dark"] .sun {
    display: none;
}

:root[data-theme="dark"] .moon {
    display: block;
}

.mode-toggle input[type="checkbox"] {
    display: none;
}
</style>