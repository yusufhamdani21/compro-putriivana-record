<template>
    <nav :class="{ scrolled: isScrolled }">
        <RouterLink to="/" class="nav-logo">
            <span class="dot" />
            Putri Ivana Record
        </RouterLink>
        <ul class="nav-links">
            <li v-for="link in links" :key="link.href">
                <a :href="link.href" @click.prevent="scrollTo(link.href)">{{ link.label }}</a>
            </li>
        </ul>
        <button class="burger" @click="menuOpen = !menuOpen">
            <span /><span /><span />
        </button>
        <div class="mobile-menu" :class="{ open: menuOpen }">
            <a v-for="link in links" :key="link.href" :href="link.href" @click.prevent="mobileNav(link.href)">{{
                link.label }}</a>
        </div>
    </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRouter, useRoute } from 'vue-router'

const router = useRouter()
const route = useRoute()

const isScrolled = ref(false)
const menuOpen = ref(false)

const links = [
    { href: '#about', label: 'Tentang' },
    { href: '#services', label: 'Layanan' },
    { href: '#artists', label: 'Artis' },
    { href: '#contact', label: 'Kontak' },
]

function scrollTo(href) {
    if (route.name !== 'Home') {
        router.push('/').then(() => {
            setTimeout(() => document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' }), 100)
        })
    } else {
        document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
    }
}

function mobileNav(href) {
    menuOpen.value = false
    scrollTo(href)
}

function onScroll() {
    isScrolled.value = window.scrollY > 40
}

onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    padding: 24px 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    transition: background var(--transition), padding var(--transition);
    background: linear-gradient(to bottom, rgba(10, 22, 40, 0.95), transparent);
}

nav.scrolled {
    padding: 16px 60px;
    background: rgba(10, 22, 40, 0.97);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(46, 116, 232, 0.1);
}

.nav-logo {
    font-family: var(--font-display);
    font-size: 1.4rem;
    font-weight: 600;
    letter-spacing: 0.04em;
    display: flex;
    align-items: center;
    gap: 10px;
    color: var(--white);
}

.dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--gold);
    display: inline-block;
    flex-shrink: 0;
}

.nav-links {
    display: flex;
    gap: 36px;
}

.nav-links a {
    color: var(--blue-light);
    font-size: 0.82rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    transition: color var(--transition);
}

.nav-links a:hover {
    color: var(--white);
}

.burger {
    display: none;
    flex-direction: column;
    gap: 5px;
    padding: 4px;
}

.burger span {
    display: block;
    width: 24px;
    height: 2px;
    background: var(--white);
    border-radius: 2px;
    transition: all var(--transition);
}

.mobile-menu {
    display: none;
    position: fixed;
    inset: 0;
    top: 64px;
    background: rgba(10, 22, 40, 0.98);
    backdrop-filter: blur(16px);
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 32px;
}

.mobile-menu.open {
    display: flex;
}

.mobile-menu a {
    font-family: var(--font-display);
    font-size: 2rem;
    font-weight: 300;
    color: var(--white);
    letter-spacing: 0.06em;
    transition: color var(--transition);
}

.mobile-menu a:hover {
    color: var(--blue-sky);
}

@media (max-width: 768px) {
    nav {
        padding: 20px 24px;
    }

    nav.scrolled {
        padding: 14px 24px;
    }

    .nav-links {
        display: none;
    }

    .burger {
        display: flex;
    }
}
</style>