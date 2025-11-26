<template>
  <section class="hero">
    <div class="container hero-container">
      <div class="hero-content">
        <h1 class="hero-title">
          Turn Your iGaming Affiliate Traffic Into <span class="text-primary">Profitable Players</span>
        </h1>
        <p class="hero-subtitle">
          We drive casino traffic and betting influencer campaigns that acquire high-value FTDs for operators. Join our proven iGaming affiliate marketing network.
        </p>
        <div class="hero-actions">
          <button class="btn btn-primary">Get Your FREE Marketing Consultation</button>
          <button class="btn btn-outline">Watch Us in Action (2 min)</button>
        </div>
        
        <div class="hero-stats">
            <div class="stat-item">
                <span class="stat-value text-primary">+2.5M</span>
                <span class="stat-label">CLICKS</span>
            </div>
            <div class="stat-item">
                <span class="stat-value text-primary">+35,000</span>
                <span class="stat-label">REGISTRATIONS</span>
            </div>
            <div class="stat-item">
                <span class="stat-value text-primary">+12,000</span>
                <span class="stat-label">FTD'S</span>
            </div>
        </div>
      </div>
    </div>
    <div class="hero-background">
        <!-- Abstract background elements could go here -->
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  padding: 160px 0 100px;
  min-height: 90vh;
  display: flex;
  flex-direction: column; /* Ensure vertical stacking if needed, or keep row but center */
  justify-content: center; /* Center vertically if column, or horizontally if row? Wait. */
  align-items: center;
  overflow: hidden;
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
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: var(--spacing-lg);
  letter-spacing: -0.03em;
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

.hero-stats {
    display: flex;
    justify-content: center;
    gap: var(--spacing-xl);
    flex-wrap: wrap;
}

.stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: var(--spacing-lg);
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.05);
    border-radius: var(--radius-lg);
    min-width: 200px;
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
