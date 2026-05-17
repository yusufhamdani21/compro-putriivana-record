<template>
    <section id="about">
        <div class="section-inner">
            <SectionTag>Siapa Kami</SectionTag>
            <h2 class="section-title">
                Label yang Percaya pada<br>
                <em>Kekuatan Musik Sejati</em>
            </h2>

            <div class="about-grid">
                <div class="about-text">
                    <p>
                        <strong>Putri Ivana Record</strong> adalah label musik independen
                        yang berdiri dengan visi sederhana namun kuat — menghadirkan musik
                        yang jujur, berkualitas, dan mampu menyentuh hati pendengar.
                    </p>
                    <p>
                        Kami percaya bahwa setiap artis memiliki cerita unik yang layak
                        didengar. Dengan tim produksi berpengalaman dan jaringan distribusi
                        digital yang luas, kami memastikan karya setiap artis mencapai
                        audiens yang tepat.
                    </p>
                    <p>
                        Dari rekaman, mixing, mastering, hingga distribusi dan promosi —
                        kami hadir di setiap langkah perjalanan musikal para artis kami.
                    </p>
                </div>

                <div class="about-visual">
                    <div class="about-card" v-for="card in aboutCards" :key="card.title">
                        <div class="about-card-icon">{{ card.icon }}</div>
                        <h4>{{ card.title }}</h4>
                        <p>{{ card.desc }}</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import SectionTag from '../components/ui/SectionTag.vue'
import { aboutCards } from '../data/content.js'
</script>

<style scoped>
section {
    position: relative;
    z-index: 1;
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
.about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
    margin-top: 60px;
}

.about-text p {
    font-size: 1rem;
    color: var(--text-muted);
    line-height: 1.85;
    font-weight: 300;
    margin-bottom: 16px;
}

.about-text p:last-child {
    margin-bottom: 0;
}

.about-text strong {
    color: var(--blue-light);
    font-weight: 500;
}

/* ── cards ── */
.about-visual {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
}

.about-card {
    background: var(--blue-dark);
    border: 1px solid rgba(46, 116, 232, 0.12);
    padding: 28px 24px;
    transition: border-color var(--transition), transform var(--transition);
}

.about-card:first-child {
    grid-column: span 2;
}

.about-card:hover {
    border-color: rgba(46, 116, 232, 0.4);
    transform: translateY(-4px);
}

.about-card-icon {
    font-size: 1.6rem;
    margin-bottom: 12px;
}

.about-card h4 {
    font-family: var(--font-display);
    font-size: 1.1rem;
    margin-bottom: 8px;
    font-weight: 400;
}

.about-card p {
    font-size: 0.82rem;
    color: var(--text-muted);
    line-height: 1.6;
}

/* ── mobile ── */
@media (max-width: 768px) {
    .section-inner {
        padding: 70px 24px;
    }

    .about-grid {
        grid-template-columns: 1fr;
        gap: 40px;
    }

    .about-visual {
        grid-template-columns: 1fr;
    }

    .about-card:first-child {
        grid-column: span 1;
    }
}
</style>