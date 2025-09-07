<template>
    <svg class="sun-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50" width="32" height="32"
        fill="currentColor">
        <!-- Núcleo fijo -->
        <circle cx="25" cy="25" r="8" class="sun-core" />

        <!-- Rayos giratorios -->
        <g class="sun-rays">
            <line x1="25" y1="5" x2="25" y2="12" />
            <line x1="25" y1="45" x2="25" y2="38" />
            <line x1="5" y1="25" x2="12" y2="25" />
            <line x1="45" y1="25" x2="38" y2="25" />

            <line x1="12" y1="12" x2="17" y2="17" />
            <line x1="38" y1="38" x2="33" y2="33" />
            <line x1="12" y1="38" x2="17" y2="33" />
            <line x1="38" y1="12" x2="33" y2="17" />
        </g>
    </svg>
</template>

<style scoped>
.sun-icon {
    color: white;
    /* o usa var(--color-text) */
    display: block;
}

.sun-core {
    fill: currentColor;
}

.sun-rays {
    stroke: currentColor;
    stroke-width: 2;
    stroke-linecap: round;
    transform-origin: center center;
    animation: spin 12s linear infinite;
    will-change: transform;
    /* ⚡ optimización GPU */
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
</style>
