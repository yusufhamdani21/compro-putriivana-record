<template>
  <NavBar />
  <RouterView />
  <FooterBar />
</template>

<script setup>
import NavBar from './components/layout/NavBar.vue'
import FooterBar from './components/layout/FooterBar.vue'
</script>