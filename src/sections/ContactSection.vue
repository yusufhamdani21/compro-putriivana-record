<template>
    <section id="contact">
        <div class="contact-inner">
            <SectionTag center>Hubungi Kami</SectionTag>
            <h2 class="section-title">
                Mari Berkolaborasi &amp;<br>
                <em>Ciptakan Sesuatu</em>
            </h2>
            <p class="contact-desc">
                Apakah kamu seorang artis yang ingin bergabung, atau brand yang ingin
                berkolaborasi? Kami selalu terbuka untuk percakapan yang bermakna.
            </p>

            <div class="contact-links">
                <a :href="`mailto:${contact.email}`" class="contact-link">
                    <span class="icon">✉</span>
                    Email Kami
                </a>
                <a :href="contact.instagram" target="_blank" class="contact-link">
                    <span class="icon">◎</span>
                    Instagram
                </a>
                <a :href="contact.whatsapp" target="_blank" class="contact-link">
                    <span class="icon">✆</span>
                    WhatsApp
                </a>
            </div>

            <div class="contact-divider" />

            <p class="contact-address">
                Bandung, Jawa Barat, Indonesia
            </p>
        </div>
    </section>
</template>

<script setup>
import SectionTag from '../components/ui/SectionTag.vue'
import { contact } from '../data/content.js'
</script>

<style scoped>
section {
    position: relative;
    z-index: 1;
}

.contact-inner {
    max-width: 700px;
    margin: 0 auto;
    padding: var(--section-pad);
    text-align: center;
}

.section-title {
    font-family: var(--font-display);
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 300;
    line-height: 1.1;
    margin-bottom: 20px;
}

.section-title em {
    font-style: italic;
    color: var(--blue-sky);
}

.contact-desc {
    color: var(--text-muted);
    line-height: 1.75;
    font-size: 0.95rem;
    margin-bottom: 44px;
}

/* ── links ── */
.contact-links {
    display: flex;
    justify-content: center;
    gap: 14px;
    flex-wrap: wrap;
}

.contact-link {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 13px 28px;
    border: 1px solid rgba(90, 156, 245, 0.25);
    border-radius: var(--radius);
    color: var(--blue-light);
    font-size: 0.82rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: all var(--transition);
}

.contact-link:hover {
    background: rgba(46, 116, 232, 0.15);
    border-color: var(--blue-bright);
    color: var(--white);
    transform: translateY(-2px);
}

.icon {
    font-size: 1rem;
}

/* ── divider ── */
.contact-divider {
    width: 40px;
    height: 1px;
    background: rgba(90, 156, 245, 0.2);
    margin: 44px auto;
}

.contact-address {
    font-size: 0.78rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--text-muted);
}

/* ── mobile ── */
@media (max-width: 768px) {
    .contact-inner {
        padding: 70px 24px;
    }

    .contact-links {
        flex-direction: column;
        align-items: center;
    }

    .contact-link {
        width: 100%;
        justify-content: center;
    }
}
</style>