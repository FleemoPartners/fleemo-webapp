<script setup>
import { ref } from 'vue';

const services = [
  {
    title: 'Marketing para empresas',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="M18.7 8l-5.1 5.2-2.8-2.7L7 14.3"/></svg>`
  },
  {
    title: 'Desarrollo de paginas web para creadores y empresas',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>`
  },
  {
    title: 'Ayuda para impulsar tus vistas como creador',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"/></svg>`
  },
  {
    title: 'Edición de videos',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`
  },
  {
    title: 'Fotos y videos empresariales para la marca',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 19l7-7 3 3-7 7-3-3z"/><path d="M18 13l-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"/><path d="M2 2l7.586 7.586"/><circle cx="11" cy="11" r="2"/></svg>`
  },
  {
    title: 'Asesoramiento de marketing digital',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a10 10 0 0 1 10 10c0 5.523-4.477 10-10 10S2 17.523 2 12 6.477 2 12 2z"/><path d="M8 14s1.5 2 4 2 4-2 4-2"/><line x1="9" y1="9" x2="9.01" y2="9"/><line x1="15" y1="9" x2="15.01" y2="9"/></svg>`
  },
  {
    title: 'No se que poner xd',
    subtitle: '10 opciones disponibles',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="14" rx="2" ry="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/></svg>`
  }
];
</script>

<template>
  <section class="services-section">
    <div class="container">
      <div class="header">
        <span class="subtitle">NUESTROS SERVICIOS</span>
        <h2 class="title">Mejora tu productividad <br>Con los mejores servicios</h2>
      </div>

      <div class="services-grid">
        <div v-for="(service, index) in services" :key="index" class="service-card">
          <div class="icon-wrapper" v-html="service.icon"></div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-subtitle">{{ service.subtitle }}</p>
        </div>

        <!-- Last "More" Card -->
        <div class="service-card more-card">
          <div class="more-content">
            <span class="plus-icon">+4</span>
            <span class="more-text">Más</span>
            <span class="more-subtitle">Ver todos los servicios</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
  padding: var(--spacing-xxl) 0;
  background: 
    radial-gradient(circle at 0% 0%, rgba(0, 255, 157, 0.03) 0%, transparent 50%),
    radial-gradient(circle at 100% 100%, rgba(0, 100, 255, 0.03) 0%, transparent 50%),
    linear-gradient(180deg, #0a0a0a 0%, #111111 100%);
  position: relative;
  overflow: hidden;
}

.services-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: radial-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 1px);
  background-size: 24px 24px;
  opacity: 0.5;
  pointer-events: none;
}

.header {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}

.subtitle {
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--color-primary);
  display: block;
  margin-bottom: var(--spacing-sm);
}

.title {
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.2;
  color: var(--color-text);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: var(--spacing-md);
}

@media (min-width: 768px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

.service-card {
  background: var(--glass-bg);
  border: var(--glass-border);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  transition: all var(--transition-normal);
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: var(--spacing-md);
  min-height: 200px;
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.05) 0%, transparent 100%);
  opacity: 0;
  transition: opacity var(--transition-normal);
}

.service-card:hover {
  transform: translateY(-5px);
  border-color: rgba(0, 255, 157, 0.3);
  box-shadow: var(--shadow-glow);
}

.service-card:hover::before {
  opacity: 1;
}

.icon-wrapper {
  width: 48px;
  height: 48px;
  background: rgba(255, 255, 255, 0.03);
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-text);
  transition: all var(--transition-fast);
  border: 1px solid rgba(255, 255, 255, 0.05);
}

.icon-wrapper :deep(svg) {
  width: 24px;
  height: 24px;
}

.service-title {
  font-size: 1.125rem;
  font-weight: 600;
  color: var(--color-text);
  margin-top: auto;
  transition: color var(--transition-fast);
}

.service-subtitle {
  font-size: 0.875rem;
  color: var(--color-text-muted);
  transition: color var(--transition-fast);
}

/* Hover States */
.service-card:hover .service-title {
  color: var(--color-primary);
}

.service-card:hover .icon-wrapper {
  color: var(--color-primary);
  background: rgba(0, 255, 157, 0.1);
  border-color: var(--color-primary);
}

/* More Card Specifics */
.more-card {
  background: var(--gradient-primary);
  border: none;
  justify-content: center;
  align-items: center;
}

.more-card .more-content {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-xs);
  z-index: 1;
}

.more-card .plus-icon {
  font-size: 2rem;
  font-weight: 700;
  color: #000;
}

.more-card .more-text {
  font-size: 1.25rem;
  font-weight: 600;
  color: #000;
}

.more-card .more-subtitle {
  font-size: 0.875rem;
  color: rgba(0, 0, 0, 0.7);
}

.more-card:hover {
  transform: translateY(-5px) scale(1.02);
  box-shadow: 0 0 30px rgba(0, 255, 157, 0.4);
}
</style>
