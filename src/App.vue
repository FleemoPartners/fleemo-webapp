<script setup>
import TheHeader from './shared/components/layout/TheHeader.vue';
import TheFooter from './shared/components/layout/TheFooter.vue';
import HomeView from './modules/home/views/HomeView.vue';
</script>

<template>
  <TheHeader />
  <main>
    <HomeView />
  </main>
  <TheFooter />
</template>

<style>

@import './assets/styles/main.css';
</style>
