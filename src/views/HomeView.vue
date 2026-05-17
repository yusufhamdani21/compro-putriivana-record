<template>
    <main>
        <HeroSection />
        <MarqueeDivider :items="marquee1" />
        <AboutSection />
        <ServicesSection />
        <MarqueeDivider :items="marquee2" reverse />
        <ArtistsSection />
        <ContactSection />
    </main>
</template>

<script setup>
import HeroSection from '../sections/HeroSection.vue'
import AboutSection from '../sections/AboutSection.vue'
import ServicesSection from '../sections/ServicesSection.vue'
import ArtistsSection from '../sections/ArtistsSection.vue'
import ContactSection from '../sections/ContactSection.vue'
import MarqueeDivider from '../components/ui/MarqueeDivider.vue'
import { marquee1, marquee2 } from '../data/content.js'
</script>