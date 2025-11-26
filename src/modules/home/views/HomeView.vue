<script setup>
import HeroSection from '../components/HeroSection.vue';
import FoundersSection from '../components/FoundersSection.vue';
import ContactSection from '../components/ContactSection.vue';
import ServicesSection from '../components/ServicesSection.vue';
</script>

<template>
  <div class="home-view">
    <section id="home">
      <HeroSection />
    </section>
    <section id="team">
      <FoundersSection />
    </section>
    <section id="services">
      <ServicesSection />
    </section>
    <section id="contact">
      <ContactSection />
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
