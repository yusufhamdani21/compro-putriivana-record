<template>
    <p class="section-tag">
        <span class="line"></span>
        <slot />
    </p>
</template>

<style scoped>
.section-tag {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 0.7rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 16px;
}

.line {
    display: block;
    width: 24px;
    height: 1px;
    background: var(--gold);
    flex-shrink: 0;
}
</style>