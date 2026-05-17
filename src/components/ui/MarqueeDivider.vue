<template>
    <div class="divider">
        <div class="track" :class="{ reverse }">
            <span v-for="(item, i) in [...items, ...items]" :key="i" :class="{ dot: item === '·' }">{{ item }}</span>
        </div>
    </div>
</template>

<script setup>
defineProps({
    items: { type: Array, required: true },
    reverse: { type: Boolean, default: false },
})
</script>

<style scoped>
.divider {
    overflow: hidden;
    height: 56px;
    display: flex;
    align-items: center;
    position: relative;
    z-index: 1;
    border-top: 1px solid rgba(46, 116, 232, 0.06);
    border-bottom: 1px solid rgba(46, 116, 232, 0.06);
}

.track {
    display: flex;
    gap: 0;
    white-space: nowrap;
    animation: marquee 22s linear infinite;
}

.track.reverse {
    animation-direction: reverse;
}

.track span {
    font-family: var(--font-display);
    font-size: 0.85rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: rgba(90, 156, 245, 0.22);
    padding: 0 32px;
}

.track span.dot {
    color: var(--gold);
    padding: 0 8px;
    letter-spacing: 0;
}

@keyframes marquee {
    from {
        transform: translateX(0);
    }

    to {
        transform: translateX(-50%);
    }
}
</style>