<template>
    <section id="artists">
        <div class="section-inner">
            <SectionTag>Roster Artis</SectionTag>
            <h2 class="section-title">
                Suara-Suara yang<br>
                <em>Kami Banggakan</em>
            </h2>

            <div class="artists-grid">
                <div class="artist-card" v-for="artist in artists" :key="artist.name">
                    <div class="artist-bg" :style="{ background: artist.bg }">
                        <span class="artist-emoji">{{ artist.emoji }}</span>
                        <div class="artist-rings">
                            <span /><span /><span />
                        </div>
                    </div>
                    <div class="artist-overlay">
                        <div class="artist-name">{{ artist.name }}</div>
                        <div class="artist-genre">{{ artist.genre }}</div>
                    </div>
                    <div class="artist-info">
                        <div class="name">{{ artist.name }}</div>
                        <div class="genre">{{ artist.genre }}</div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import SectionTag from '../components/ui/SectionTag.vue'
import { artists } from '../data/content.js'
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
.artists-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin-top: 60px;
}

/* ── card ── */
.artist-card {
    position: relative;
    cursor: pointer;
    border: 1px solid rgba(46, 116, 232, 0.1);
    overflow: hidden;
    transition: border-color var(--transition), transform var(--transition);
}

.artist-card:hover {
    border-color: rgba(46, 116, 232, 0.4);
    transform: translateY(-6px);
}

.artist-bg {
    aspect-ratio: 3 / 4;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    transition: transform 0.5s ease;
}

.artist-card:hover .artist-bg {
    transform: scale(1.04);
}

.artist-emoji {
    font-size: 4rem;
    position: relative;
    z-index: 2;
}

/* decorative rings inside card */
.artist-rings {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
}

.artist-rings span {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(46, 116, 232, 0.15);
}

.artist-rings span:nth-child(1) {
    width: 120px;
    height: 120px;
}

.artist-rings span:nth-child(2) {
    width: 180px;
    height: 180px;
}

.artist-rings span:nth-child(3) {
    width: 240px;
    height: 240px;
}

/* overlay on hover */
.artist-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top,
            rgba(10, 22, 40, 0.95) 0%,
            transparent 55%);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 20px;
    opacity: 0;
    transition: opacity var(--transition);
}

.artist-card:hover .artist-overlay {
    opacity: 1;
}

.artist-overlay .artist-name {
    font-family: var(--font-display);
    font-size: 1.15rem;
    font-weight: 400;
}

.artist-overlay .artist-genre {
    font-size: 0.72rem;
    letter-spacing: 0.12em;
    color: var(--blue-sky);
    text-transform: uppercase;
    margin-top: 4px;
}

/* info below card */
.artist-info {
    padding: 14px 0 4px;
    text-align: center;
}

.artist-info .name {
    font-family: var(--font-display);
    font-size: 1.05rem;
    font-weight: 400;
}

.artist-info .genre {
    font-size: 0.72rem;
    letter-spacing: 0.1em;
    color: var(--text-muted);
    text-transform: uppercase;
    margin-top: 4px;
}

/* ── mobile ── */
@media (max-width: 768px) {
    .section-inner {
        padding: 70px 24px;
    }

    .artists-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 12px;
    }
}
</style>