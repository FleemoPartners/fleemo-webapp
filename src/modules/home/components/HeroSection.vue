<template>
  <section class="hero">
    <div class="hero-glow"></div>
    <div class="container hero-container">
      <div class="hero-content">
        <h1 class="hero-title animate-fade-in">
          Haz crecer tus redes y convierte seguidores en <span class="text-gradient">Clientes Reales</span>
        </h1>
        <p class="hero-subtitle animate-fade-in delay-1">
          Impulsamos a pequeñas empresas, emprendedores e influencers emergentes a escalar en redes sociales, aumentar su visibilidad y convertir su contenido en ventas reales.
        </p>
        <div class="hero-actions animate-fade-in delay-2">
          <button class="btn btn-primary btn-glow">Get Your FREE Growth Strategy</button>
          <button class="btn btn-outline">Watch Us in Action (2 min)</button>
        </div>
        
        <div class="hero-stats animate-fade-in delay-3">
            <div class="stat-item glass-card">
                <span class="stat-value text-gradient">+2.5M</span>
                <span class="stat-label">CLICKS</span>
            </div>
            <div class="stat-item glass-card">
                <span class="stat-value text-gradient">+35,000</span>
                <span class="stat-label">REGISTRATIONS</span>
            </div>
            <div class="stat-item glass-card">
                <span class="stat-value text-gradient">+12,000</span>
                <span class="stat-label">FTD'S</span>
            </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  padding: 130px 0 80px;
  min-height: 80vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  background: radial-gradient(circle at top center, #1a1a1a 0%, #0a0a0a 100%);
}

.hero-glow {
  position: absolute;
  top: -20%;
  left: 50%;
  transform: translateX(-50%);
  width: 800px;
  height: 800px;
  background: var(--gradient-glow);
  filter: blur(80px);
  opacity: 0.4;
  pointer-events: none;
  z-index: 1;
}

.hero-container {
  position: relative;
  z-index: 2;
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.hero-title {
  font-size: 3.25rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: var(--spacing-lg);
  letter-spacing: -0.03em;
}

.text-gradient {
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
  filter: drop-shadow(0 2px 4px rgba(0, 255, 157, 0.2));
}

.hero-subtitle {
  font-size: 1.25rem;
  color: var(--color-text-muted);
  margin-bottom: var(--spacing-xl);
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.hero-actions {
  display: flex;
  gap: var(--spacing-md);
  justify-content: center;
  margin-bottom: var(--spacing-xxl);
  flex-wrap: wrap;
}

.btn-glow {
  box-shadow: 0 0 15px rgba(0, 255, 157, 0.3);
  transition: all var(--transition-normal);
}

.btn-glow:hover {
  box-shadow: 0 0 25px rgba(0, 255, 157, 0.5);
  transform: translateY(-2px);
}

.hero-stats {
    display: flex;
    justify-content: center;
    gap: var(--spacing-xl);
    flex-wrap: wrap;
}

.glass-card {
    background: var(--glass-bg);
    border: var(--glass-border);
    backdrop-filter: blur(12px);
    box-shadow: var(--shadow-card);
}

.stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: var(--spacing-lg);
    border-radius: var(--radius-lg);
    min-width: 200px;
    transition: transform var(--transition-normal);
}

.stat-item:hover {
    transform: translateY(-5px);
    border-color: rgba(0, 255, 157, 0.3);
}

.stat-value {
    font-size: 2.5rem;
    font-weight: 700;
    line-height: 1;
    margin-bottom: var(--spacing-xs);
}

.stat-label {
    font-size: 0.875rem;
    letter-spacing: 0.1em;
    color: var(--color-text-muted);
    text-transform: uppercase;
}

/* Animations */
.animate-fade-in {
  opacity: 0;
  animation: fade-in-up 0.8s ease forwards;
}

.delay-1 { animation-delay: 0.2s; }
.delay-2 { animation-delay: 0.4s; }
.delay-3 { animation-delay: 0.6s; }

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-stats {
      gap: var(--spacing-md);
  }
  
  .stat-item {
      min-width: 140px;
      padding: var(--spacing-md);
  }
  
  .stat-value {
      font-size: 1.75rem;
  }
}
</style>
