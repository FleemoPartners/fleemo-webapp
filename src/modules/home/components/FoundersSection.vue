<script setup>
import BaseCard from '@/shared/components/ui/BaseCard.vue';

const founders = [
  {
    id: 1,
    name: 'Alex Rivera',
    role: 'Co-Founder & CEO',
    image: 'https://placehold.co/400x400/1a1a1a/00ff9d?text=AR', // Placeholder
    bio: 'Visionary leader with 10+ years in iGaming affiliate marketing.'
  },
  {
    id: 2,
    name: 'Sarah Chen',
    role: 'Co-Founder & COO',
    image: 'https://placehold.co/400x400/1a1a1a/00ff9d?text=SC', // Placeholder
    bio: 'Operations expert ensuring seamless campaign execution and partner satisfaction.'
  },
  {
    id: 3,
    name: 'Marcus Johnson',
    role: 'Head of Partnerships',
    image: 'https://placehold.co/400x400/1a1a1a/00ff9d?text=MJ', // Placeholder
    bio: 'Building strong relationships with top-tier operators and influencers globally.'
  }
];
</script>

<template>
  <section class="founders">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Meet the <span class="text-primary">Founders</span></h2>
        <p class="section-subtitle">The team behind the success.</p>
      </div>
      
      <div class="founders-grid">
        <BaseCard v-for="founder in founders" :key="founder.id" class="founder-card">
          <div class="founder-image-wrapper">
            <img :src="founder.image" :alt="founder.name" class="founder-image">
          </div>
          <div class="founder-content">
            <h3 class="founder-name">{{ founder.name }}</h3>
            <p class="founder-role text-primary">{{ founder.role }}</p>
            <p class="founder-bio">{{ founder.bio }}</p>
          </div>
        </BaseCard>
      </div>
    </div>
  </section>
</template>

<style scoped>
.founders {
  padding: 100px 0;
  background-color: #0d0d0d; /* Slightly lighter than main bg */
}

.section-header {
  text-align: center;
  margin-bottom: var(--spacing-xxl);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: var(--spacing-sm);
}

.section-subtitle {
  color: var(--color-text-muted);
  font-size: 1.1rem;
}

.founders-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: var(--spacing-lg);
}

.founder-card {
  flex: 1 1 300px;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  height: 100%;
}

.founder-image-wrapper {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  overflow: hidden;
  margin-bottom: var(--spacing-md);
  border: 2px solid var(--color-primary);
  padding: 4px; /* Space between border and image */
}

.founder-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
  background-color: var(--color-surface);
}

.founder-name {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: var(--spacing-xs);
}

.founder-role {
  font-size: 0.9rem;
  font-weight: 500;
  margin-bottom: var(--spacing-md);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.founder-bio {
  color: var(--color-text-muted);
  font-size: 0.95rem;
  line-height: 1.5;
}
</style>
