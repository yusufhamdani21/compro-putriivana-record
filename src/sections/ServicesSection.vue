<template>
    <section id="services" class="services">
        <div class="section-inner">
            <SectionTag>Layanan Kami</SectionTag>
            <h2 class="section-title">
                Dari Studio hingga<br>
                <em>Panggung Dunia</em>
            </h2>

            <div class="services-grid">
                <div class="service-item" v-for="(svc, i) in services" :key="svc.title">
                    <div class="service-num">{{ String(i + 1).padStart(2, '0') }}</div>
                    <h3>{{ svc.title }}</h3>
                    <p>{{ svc.desc }}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import SectionTag from '../components/ui/SectionTag.vue'
import { services } from '../data/content.js'
</script>

<style scoped>
.services {
    position: relative;
    z-index: 1;
    background: linear-gradient(to bottom,
            transparent,
            rgba(26, 58, 107, 0.15),
            transparent);
}

.section-inner {
    max-width: var(--max-width);
    margin: 0 auto;
    padding: var(--section-pad);
}

.section-title {
    font-family: var(--font-display);
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 300;
    line-height: 1.1;
}

.section-title em {
    font-style: italic;
    color: var(--blue-sky);
}

/* ── grid ── */
.services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    margin-top: 60px;
    border: 1px solid rgba(46, 116, 232, 0.1);
}

.service-item {
    padding: 44px 36px;
    background: rgba(13, 31, 60, 0.6);
    border-right: 1px solid rgba(46, 116, 232, 0.08);
    position: relative;
    overflow: hidden;
    transition: background var(--transition);
}

.service-item::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(to right, var(--blue-bright), transparent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s ease;
}

.service-item:hover {
    background: rgba(26, 58, 107, 0.5);
}

.service-item:hover::before {
    transform: scaleX(1);
}

.service-num {
    font-family: var(--font-display);
    font-size: 3rem;
    font-weight: 300;
    color: rgba(46, 116, 232, 0.2);
    line-height: 1;
    margin-bottom: 20px;
}

.service-item h3 {
    font-family: var(--font-display);
    font-size: 1.25rem;
    font-weight: 400;
    margin-bottom: 12px;
}

.service-item p {
    font-size: 0.84rem;
    color: var(--text-muted);
    line-height: 1.7;
}

/* ── mobile ── */
@media (max-width: 768px) {
    .section-inner {
        padding: 70px 24px;
    }

    .services-grid {
        grid-template-columns: 1fr;
    }

    .service-item {
        border-right: none;
    }
}
</style>