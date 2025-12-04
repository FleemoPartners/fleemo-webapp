<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import fleemoLogo from '@/assets/fleemo.svg';

const isMenuOpen = ref(false);
const isScrolled = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const checkScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const scrollToSection = (id) => {
  isMenuOpen.value = false;
  const element = document.querySelector(id);
  if (element) {
    const offset = 80;
    const bodyRect = document.body.getBoundingClientRect().top;
    const elementRect = element.getBoundingClientRect().top;
    const elementPosition = elementRect - bodyRect;
    const offsetPosition = elementPosition - offset;

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth'
    });
  }
};

onMounted(() => {
  window.addEventListener('scroll', checkScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', checkScroll);
});
</script>

<template>
  <header class="header" :class="{ 'header-scrolled': isScrolled }">
    <div class="container header-container">
      <a href="#" @click.prevent="scrollToSection('#home')" class="logo">
        <span class="logo-icon">
             <img :src="fleemoLogo" alt="Fleemo Partners" class="logo-img" />
        </span>
        <span>Fleemo<span class="text-gradient">Partners  </span></span>
      </a>

      <nav class="nav" :class="{ 'is-open': isMenuOpen }">
        <ul class="nav-list">
          <li class="nav-item"><a href="#home" @click.prevent="scrollToSection('#home')" class="nav-link">Home</a></li>
          <li class="nav-item"><a href="#team" @click.prevent="scrollToSection('#team')" class="nav-link">Team</a></li>
          <li class="nav-item"><a href="#services" @click.prevent="scrollToSection('#services')" class="nav-link">Services</a></li>
          <li class="nav-item"><a href="#contact" @click.prevent="scrollToSection('#contact')" class="nav-link">Contact</a></li>
        </ul>
        <div class="nav-actions">
             <button class="btn btn-primary" @click="scrollToSection('#contact')">Get Started</button>
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
  padding: 20px 0;
  transition: all 0.3s ease;
  background: transparent;
  border-bottom: 1px solid transparent;
}

.header-scrolled {
  background: rgba(10, 10, 10, 0.8);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  padding: 15px 0;
}

.header-scrolled::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent 0%, rgba(0, 255, 157, 0.3) 50%, transparent 100%);
  opacity: 0.5;
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
  transition: transform var(--transition-fast);
  text-decoration: none;
  color: var(--color-text);
}

.logo:hover {
  transform: scale(1.02);
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
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 300;
  filter: drop-shadow(0 0 10px rgba(0, 255, 157, 0.3));
}

.nav-link {
  font-size: 0.95rem;
  font-weight: 500;
  color: var(--color-text-muted);
  position: relative;
  padding: 4px 0;
  transition: color var(--transition-fast);
  text-decoration: none;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--color-primary);
  transition: width var(--transition-fast);
  box-shadow: 0 0 5px rgba(0, 255, 157, 0.5);
}

.nav-link:hover {
  color: var(--color-text);
}

.nav-link:hover::after {
  width: 100%;
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
