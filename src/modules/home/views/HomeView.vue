<script setup>
import HeroSection from '../components/HeroSection.vue';
import FoundersSection from '../components/FoundersSection.vue';
</script>

<template>
  <div class="home-view">
    <section id="home">
      <HeroSection />
    </section>
    <section id="team">
      <FoundersSection />
    </section>
  </div>
</template>

<style scoped>
.home-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

:deep(section) {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

:deep(.container) {
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
}
</style>
