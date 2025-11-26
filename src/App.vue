<script setup>
import TheHeader from './shared/components/layout/TheHeader.vue';
import HomeView from './modules/home/views/HomeView.vue';
</script>

<template>
  <TheHeader />
  <main>
    <HomeView />
  </main>
</template>

<style>
@import './assets/styles/main.css';
</style>
