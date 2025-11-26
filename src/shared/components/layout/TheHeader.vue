<script setup>
import { ref } from 'vue';
import logo from '@/assets/logo.png';

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
  <header class="header">
    <div class="container header-container">
      <a href="#" class="logo">
        <span class="logo-icon">
             <img :src="logo" alt="Fleemo Partners Logo" class="logo-img" />
        </span>
        <span class="logo-text">FLEEMO <span class="logo-highlight">PARTNERS</span></span>
      </a>

      <nav class="nav" :class="{ 'is-open': isMenuOpen }">
        <ul class="nav-list">
          <li class="nav-item"><a href="#home" class="nav-link">Home</a></li>
          <li class="nav-item"><a href="#team" class="nav-link">Team</a></li>
          <li class="nav-item"><a href="#services" class="nav-link">Services</a></li>
          <li class="nav-item"><a href="#contact" class="nav-link">Contact</a></li>
        </ul>
        <div class="nav-actions">
             <button class="btn btn-primary">Get Started</button>
        </div>
      </nav>

      <button class="menu-toggle" @click="toggleMenu" aria-label="Toggle Menu">
        <span class="hamburger"></span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background-color: #262626;
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  padding: var(--spacing-md) 0;
}

.header-container {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
}

.logo {
  justify-self: start;
  display: flex;
  align-items: center;
  gap: var(--spacing-sm);
  font-weight: 700;
  font-size: 1.5rem;
  letter-spacing: -0.02em;
}

.nav {
  display: contents;
}

.nav-list {
  justify-self: center;
  display: flex;
  align-items: center;
  gap: var(--spacing-lg);
}

.nav-actions {
  justify-self: end;
}

.menu-toggle {
  display: none;
  justify-self: end;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--spacing-sm);
}

.logo-img {
  width: 32px;
  height: 32px;
  object-fit: contain;
}

.logo-highlight {
  color: var(--color-primary);
  font-weight: 300;
}

.nav-link {
  font-size: 0.95rem;
  font-weight: 500;
  color: var(--color-text-muted);
}

.nav-link:hover {
  color: var(--color-primary);
}

.hamburger {
  display: block;
  width: 24px;
  height: 2px;
  background-color: var(--color-text);
  position: relative;
}

.hamburger::before,
.hamburger::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: var(--color-text);
  left: 0;
  transition: transform var(--transition-fast);
}

.hamburger::before { top: -6px; }
.hamburger::after { bottom: -6px; }

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
    grid-column: 3; /* Ensure it stays on the right */
  }

  .nav {
    display: flex; /* Restore flex for mobile drawer */
    position: fixed;
    top: 70px;
    left: 0;
    width: 100%;
    height: calc(100vh - 70px);
    background-color: var(--color-background);
    flex-direction: column;
    padding: var(--spacing-xl) var(--spacing-md);
    transform: translateX(100%);
    transition: transform var(--transition-normal);
    z-index: 999;
  }

  .nav.is-open {
    transform: translateX(0);
  }

  .nav-list {
    flex-direction: column;
    width: 100%;
    text-align: center;
    justify-self: auto; /* Reset grid prop */
  }
  
  .nav-actions {
    margin-top: var(--spacing-lg);
    justify-self: auto; /* Reset grid prop */
  }
}
</style>
