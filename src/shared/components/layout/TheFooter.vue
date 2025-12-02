<script setup>
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
};
</script>

<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-top">
        <!-- Brand Section -->
        <div class="footer-column brand-column">
          <h2 class="brand-name">Fleemo Partners</h2>
          <p class="brand-subtitle">Equipo de asesoramiento de redes</p>
        </div>

        <!-- Links Section -->
        <div class="footer-column">
          <h3 class="column-title">ENLACES</h3>
          <ul class="footer-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#team">Team</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
            <li><a href="#about">About</a></li>
          </ul>
        </div>

        <!-- Contact Section -->
        <div class="footer-column">
          <h3 class="column-title">CONTACTO</h3>
          <ul class="footer-links">
            <li><a href="mailto:fleemocontacto@gmail.com">fleemocontacto@gmail.com</a></li>
            <li><a href="https://www.linkedin.com/company/fleemopartners/posts/?feedView=all">LinkedIn</a></li>
          </ul>
        </div>
      </div>

      <!-- Social Section -->
      <div class="footer-social">
        <h3 class="column-title">SÍGUEME</h3>
        <div class="social-icons">
          <a href="https://www.linkedin.com/company/fleemopartners/posts/?feedView=all" class="social-icon" aria-label="LinkedIn">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
          </a>
          <a href="https://www.instagram.com/fleemopartners/" class="social-icon" aria-label="Instagram">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
          </a>
          <a href="https://www.tiktok.com/@fleemopartners?_r=1&_t=ZS-91s5zVaSGu5" class="social-icon" aria-label="TikTok">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"></path></svg>
          </a>
        </div>
      </div>

      <div class="footer-divider"></div>

      <div class="footer-bottom">
        <p class="copyright">© 2025 Fleemo Partners. Todos los derechos reservados.</p>
        <div class="footer-bottom-right">
           <p class="developed-by">Developed by <a class="text-primary" href="https://fleemo.com">FleemoSoftware</a></p>
           <p class="made-with">Hecho con <span class="heart">❤</span> usando Vue.js</p>
        </div>
      </div>
      
      <button class="scroll-top-btn" @click="scrollToTop" aria-label="Volver arriba">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="19" x2="12" y2="5"></line><polyline points="5 12 12 5 19 12"></polyline></svg>
      </button>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #000000;
  color: var(--color-text);
  padding: var(--spacing-xxl) 0 var(--spacing-lg);
  position: relative;
  font-family: var(--font-family-sans);
}

.footer::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent 0%, var(--color-primary) 50%, transparent 100%);
  opacity: 0.5;
}

.footer-top {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xl);
  margin-bottom: var(--spacing-xl);
}

.footer-column {
  flex: 1;
  min-width: 200px;
}

.brand-column {
  flex: 2; /* Take more space */
}

.brand-name {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: var(--spacing-xs);
  color: var(--color-text);
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.brand-subtitle {
  color: var(--color-text-muted);
  font-size: 0.9rem;
}

.column-title {
  font-size: 0.875rem;
  font-weight: 700;
  text-transform: uppercase;
  margin-bottom: var(--spacing-md);
  color: var(--color-text);
  letter-spacing: 0.05em;
}

.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: var(--spacing-sm);
}

.footer-links a {
  color: var(--color-text-muted);
  text-decoration: none;
  font-size: 0.9rem;
  transition: all var(--transition-fast);
}

.footer-links a:hover {
  color: var(--color-primary);
  padding-left: 5px;
}

.footer-social {
  margin-bottom: var(--spacing-xl);
}

.social-icons {
  display: flex;
  gap: var(--spacing-md);
}

.social-icon {
  color: var(--color-text-muted);
  transition: all var(--transition-fast);
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.05);
  border: 1px solid transparent;
}

.social-icon:hover {
  color: var(--color-primary);
  background-color: rgba(0, 255, 157, 0.1);
  border-color: var(--color-primary);
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 255, 157, 0.2);
}

.footer-divider {
  height: 1px;
  background: linear-gradient(90deg, transparent 0%, rgba(255, 255, 255, 0.1) 50%, transparent 100%);
  margin-bottom: var(--spacing-lg);
}

.footer-bottom {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
  color: var(--color-text-muted);
  font-size: 0.8rem;
  align-items: flex-start;
}

@media (min-width: 768px) {
  .footer-bottom {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
  
  .footer-bottom-right {
      display: flex;
      gap: var(--spacing-lg);
      align-items: center;
  }
}

.text-primary {
  color: var(--color-primary);
  font-weight: 600;
}

.heart {
  color: #ef4444;
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}

.scroll-top-btn {
  position: absolute;
  bottom: var(--spacing-lg);
  right: var(--spacing-lg);
  background-color: var(--color-surface);
  color: var(--color-text);
  border: 1px solid var(--color-border);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all var(--transition-fast);
}

.scroll-top-btn:hover {
  background-color: var(--color-primary);
  color: #000;
  border-color: var(--color-primary);
  box-shadow: 0 0 15px rgba(0, 255, 157, 0.4);
  transform: translateY(-3px);
}

@media (max-width: 768px) {
  .footer-top {
    flex-direction: column;
    gap: var(--spacing-lg);
  }
  
  .scroll-top-btn {
    bottom: var(--spacing-md);
    right: var(--spacing-md);
  }
}
</style>
