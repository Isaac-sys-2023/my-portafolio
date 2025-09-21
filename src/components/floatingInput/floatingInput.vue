<template>
    <div class="input-wrapper">
        <component :is="props.isTextarea ? 'textarea' : 'input'" :type="props.isTextarea ? undefined : props.type"
            :id="props.id" :rows="props.isTextarea ? props.rows : undefined" :placeholder="''" :value="props.modelValue"
            @input="$emit('update:modelValue', $event.target.value)" class="input-field" :class="inputBorderClass"
            autocomplete="off" required />

        <label :for="props.id" class="input-label" :class="labelColorClass">
            {{ props.label }}
        </label>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    modelValue: String,
    label: String,
    id: String,
    type: {
        type: String,
        default: 'text'
    },
    borderColor: {
        type: String,
        default: 'purple'
    },
    isTextarea: {
        type: Boolean,
        default: false
    },
    rows: {
        type: Number,
        default: 4
    }
});

defineEmits(['update:modelValue']);

const inputBorderClass = computed(() => `focus-border-${props.borderColor}`);
const labelColorClass = computed(() => `label-focus-${props.borderColor}`);
</script>

<style scoped>
/* Wrapper */
.input-wrapper {
    position: relative;
    z-index: 0;
    width: 100%;
}

/* Input / Textarea base styles */
.input-field {
    display: block;
    width: 100%;
    padding-top: 0.75rem;
    /* pt-3 */
    padding-bottom: 0.5rem;
    /* pb-2 */
    padding-left: 0;
    padding-right: 0;
    background: transparent;
    border: none;
    border-bottom: 2px solid var(--color-heading);
    /* gray-700 */
    color: var(--color-text);
    appearance: none;
    outline: none;
}

/* Label */
.input-label {
    position: absolute;
    top: 0.75rem;
    /* top-3 */
    left: 0;
    color: var(--color-heading);
    /* gray-400 */
    transform-origin: 0 0;
    transform: scale(0.75) translateY(-1.5rem);
    transition: all 0.3s ease;
    pointer-events: none;
    z-index: -10;
}

/* Placeholder-shown (simula peer-placeholder-shown) */
.input-field:placeholder-shown+.input-label {
    transform: scale(1) translateY(0);
}

/* Focused state (simula peer-focus) */
.input-field:focus+.input-label {
    transform: scale(0.75) translateY(-1.5rem);
}

/* Focus border color classes */
.focus-border-purple:focus {
    border-bottom-color: var(--color-primary);
}

.focus-border-red:focus {
    border-bottom-color: #ef4444;
}

.focus-border-pink:focus {
    border-bottom-color: #ec4899;
}

/* Label color on focus */
.input-field:focus+.label-focus-purple {
    color: var(--color-primary);
}

.input-field:focus+.label-focus-red {
    color: #ef4444;
}

.input-field:focus+.label-focus-pink {
    color: #ec4899;
}
</style>
