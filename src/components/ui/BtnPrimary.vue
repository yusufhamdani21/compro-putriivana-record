<template>
    <button :class="['btn', variant]" @click="$emit('click')">
        <slot />
    </button>
</template>

<script setup>
defineProps({
    variant: {
        type: String,
        default: 'primary'
    }
})
defineEmits(['click'])
</script>

<style scoped>
.btn {
    padding: 14px 36px;
    border-radius: var(--radius);
    font-family: var(--font-body);
    font-size: 0.82rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: all var(--transition);
}

.primary {
    background: var(--blue-bright);
    color: var(--white);
    border: none;
}

.primary:hover {
    background: var(--blue-sky);
    transform: translateY(-2px);
}

.ghost {
    background: transparent;
    color: var(--blue-light);
    border: 1px solid rgba(90, 156, 245, 0.3);
}

.ghost:hover {
    border-color: var(--blue-sky);
    color: var(--white);
}
</style>