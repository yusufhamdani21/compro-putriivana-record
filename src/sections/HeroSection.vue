<template>
    <section class="hero">
        <!-- Vinyl circle -->
        <div class="hero-circle">
            <div class="vinyl" />
        </div>

        <p class="hero-tag">
            <span class="line" />
            Music Label · Est. 2020
        </p>

        <h1 class="hero-title">
            Suara yang<br>
            <em>Menggerakkan</em><br>
            Jiwa
        </h1>

        <p class="hero-sub">
            Label musik independen yang mendedikasikan setiap nada untuk karya
            yang autentik, artistik, dan berjiwa — dari Indonesia untuk dunia.
        </p>

        <div class="hero-cta">
            <BtnPrimary @click="scrollTo('#artists')">Temui Artis Kami</BtnPrimary>
            <BtnPrimary variant="ghost" @click="scrollTo('#contact')">Hubungi Kami</BtnPrimary>
        </div>

        <div class="hero-stats">
            <div class="stat-item" v-for="stat in stats" :key="stat.label">
                <span class="stat-num">{{ stat.num }}</span>
                <span class="stat-label">{{ stat.label }}</span>
            </div>
        </div>
    </section>
</template>

<script setup>
import BtnPrimary from '../components/ui/BtnPrimary.vue'
import { stats } from '../data/content.js'

function scrollTo(href) {
    document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<style scoped>
.hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 0 60px;
    overflow: hidden;
}

/* ── circle + vinyl ── */
.hero-circle {
    position: absolute;
    right: -8%;
    top: 50%;
    transform: translateY(-50%);
    width: 680px;
    height: 680px;
    border-radius: 50%;
    background: radial-gradient(circle at 40% 40%, var(--blue-mid) 0%, var(--blue-deep) 70%);
    border: 1px solid rgba(46, 116, 232, 0.15);
    animation: pulse 6s ease-in-out infinite;
}

.hero-circle::before {
    content: '';
    position: absolute;
    inset: 30px;
    border-radius: 50%;
    border: 1px solid rgba(46, 116, 232, 0.1);
}

.hero-circle::after {
    content: '';
    position: absolute;
    inset: 80px;
    border-radius: 50%;
    border: 1px solid rgba(46, 116, 232, 0.07);
}

@keyframes pulse {

    0%,
    100% {
        transform: translateY(-50%) scale(1);
    }

    50% {
        transform: translateY(-50%) scale(1.03);
    }
}

.vinyl {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 320px;
    height: 320px;
    border-radius: 50%;
    background: conic-gradient(from 0deg,
            #0d1f3c 0%, #162d52 15%, #0d1f3c 30%,
            #162d52 50%, #0d1f3c 65%, #162d52 80%, #0d1f3c 100%);
    border: 2px solid rgba(46, 116, 232, 0.2);
    animation: spin 20s linear infinite;
}

.vinyl::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 90px;
    height: 90px;
    border-radius: 50%;
    background: radial-gradient(circle, var(--blue-bright) 0%, var(--blue-mid) 60%);
    border: 3px solid rgba(255, 255, 255, 0.1);
}

.vinyl::after {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 14px;
    height: 14px;
    border-radius: 50%;
    background: var(--white);
}

@keyframes spin {
    to {
        transform: translate(-50%, -50%) rotate(360deg);
    }
}

/* ── text ── */
.hero-tag {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 0.72rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 20px;
}

.line {
    display: block;
    width: 30px;
    height: 1px;
    background: var(--gold);
    flex-shrink: 0;
}

.hero-title {
    font-family: var(--font-display);
    font-size: clamp(3.5rem, 7vw, 6.5rem);
    font-weight: 300;
    line-height: 1.0;
    letter-spacing: -0.01em;
    max-width: 620px;
}

.hero-title em {
    font-style: italic;
    color: var(--blue-sky);
}

.hero-sub {
    margin-top: 28px;
    max-width: 420px;
    font-size: 0.95rem;
    color: var(--text-muted);
    line-height: 1.7;
    font-weight: 300;
}

.hero-cta {
    margin-top: 44px;
    display: flex;
    gap: 16px;
    align-items: center;
}

/* ── stats ── */
.hero-stats {
    margin-top: 80px;
    display: flex;
    gap: 48px;
}

.stat-item {
    display: flex;
    flex-direction: column;
    gap: 4px;
}

.stat-num {
    font-family: var(--font-display);
    font-size: 2.2rem;
    font-weight: 600;
    color: var(--white);
}

.stat-label {
    font-size: 0.72rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--text-muted);
}

/* ── mobile ── */
@media (max-width: 768px) {
    .hero {
        padding: 120px 24px 60px;
    }

    .hero-circle {
        width: 300px;
        height: 300px;
        right: -25%;
    }

    .vinyl {
        width: 140px;
        height: 140px;
    }

    .vinyl::before {
        width: 44px;
        height: 44px;
    }

    .vinyl::after {
        width: 8px;
        height: 8px;
    }

    .hero-stats {
        gap: 28px;
        flex-wrap: wrap;
    }

    .hero-cta {
        flex-direction: column;
        align-items: flex-start;
    }
}
</style>