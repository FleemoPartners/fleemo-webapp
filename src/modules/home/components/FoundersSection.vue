<script setup>
import { ref } from 'vue';
import BaseCard from '@/shared/components/ui/BaseCard.vue';

const founders = [
  {
    id: 1,
    name: 'Francisco Hurtado',
    role: 'Co-Fundador',
    image: 'https://i.postimg.cc/W3hgn10M/1755026008117.jpg',
    bio: 'Visionary leader with 10+ years in iGaming affiliate marketing. Driving innovation and growth in the industry.'
  },
  {
    id: 2,
    name: 'Arturo Reyes',
    role: 'Co-Fundador',
    image: 'https://i.postimg.cc/YSNsH8P3/1720583786545.jpg',
    bio: 'Operations expert ensuring seamless campaign execution and partner satisfaction across all markets.'
  },
  {
    id: 3,
    name: 'Andre Valdiviezo',
    role: 'Socio Estrategico',
    image: 'https://i.postimg.cc/wM127kW6/1749573185395.jpg',
    bio: 'Building strong relationships with top-tier operators and influencers globally.'
  },
  {
    id: 4,
    name: 'Renzo Garcia',
    role: 'Socio Estrategico',
    image: 'https://placehold.co/400x400/1a1a1a/00ff9d?text=RG',
    bio: 'Creating data-driven marketing strategies that deliver exceptional results for our partners.'
  },
  {
    id: 5,
    name: 'Sebastian Quinde',
    role: 'Area de Software',
    image: 'https://placehold.co/400x400/1a1a1a/00ff9d?text=SQ',
    bio: 'Leading technical innovation and ensuring our platform stays ahead of the curve.'
  }
];

const currentIndex = ref(0);

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % founders.length;
};

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + founders.length) % founders.length;
};

const getCardClass = (index) => {
  const diff = (index - currentIndex.value + founders.length) % founders.length;
  
  if (diff === 0) return 'active';
  if (diff === 1 || diff === founders.length - 1) return 'side';
  return 'hidden';
};

const getCardStyle = (index) => {
  const diff = (index - currentIndex.value + founders.length) % founders.length;
  
  if (diff === 0) {
    return { transform: 'translateX(0) scale(1)', zIndex: 3, opacity: 1 };
  } else if (diff === 1) {
    return { transform: 'translateX(80%) scale(0.85) rotateY(-15deg)', zIndex: 2, opacity: 0.6 };
  } else if (diff === founders.length - 1) {
    return { transform: 'translateX(-80%) scale(0.85) rotateY(15deg)', zIndex: 2, opacity: 0.6 };
  } else {
    return { transform: 'translateX(0) scale(0.7)', zIndex: 1, opacity: 0 };
  }
};
</script>

<template>
  <section class="founders">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Conoce a nuestro <span class="text-primary">Equipo</span></h2>
        <p class="section-subtitle">El equipo detrás del éxito.</p>
      </div>
      
      <div class="carousel-container">
        <button class="carousel-btn prev" @click="prevSlide" aria-label="Previous">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="15 18 9 12 15 6"></polyline>
          </svg>
        </button>

        <div class="carousel-track">
          <div
            v-for="(founder, index) in founders"
            :key="founder.id"
            class="founder-card-wrapper"
            :class="getCardClass(index)"
            :style="getCardStyle(index)"
          >
            <BaseCard class="founder-card">
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

        <button class="carousel-btn next" @click="nextSlide" aria-label="Next">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="9 18 15 12 9 6"></polyline>
          </svg>
        </button>
      </div>

      <div class="carousel-dots">
        <button
          v-for="(founder, index) in founders"
          :key="`dot-${founder.id}`"
          class="dot"
          :class="{ active: index === currentIndex }"
          @click="currentIndex = index"
          :aria-label="`Go to slide ${index + 1}`"
        ></button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.founders {
  padding: 100px 0;
  background-color: #0d0d0d;
  overflow: hidden;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
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

.carousel-container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem 0;
  min-height: 550px;
}

.carousel-track {
  position: relative;
  width: 100%;
  max-width: 600px;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  perspective: 1000px;
}

.founder-card-wrapper {
  position: absolute;
  width: 100%;
  max-width: 500px;
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  transform-style: preserve-3d;
}

.founder-card-wrapper.hidden {
  pointer-events: none;
}

.founder-card {
  background: linear-gradient(135deg, rgba(80, 77, 82, 0.15) 0%, rgba(208, 207, 209, 0.15) 100%);
  border: 1px solid rgba(83, 78, 88, 0.3);
  padding: 2.5rem 2rem;
  min-height: 480px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  backdrop-filter: blur(10px);
  box-shadow: 0 20px 60px rgba(83, 78, 88, 0.2);
}

.founder-card-wrapper.active .founder-card {
  border-color: var(--color-primary);
  box-shadow: 0 25px 80px rgba(0, 255, 157, 0.3);
}

.founder-image-wrapper {
  width: 300;
  height: 320px;
  margin: 0 auto 1.5rem;
  border-radius: var(--radius-md);
  overflow: hidden;
  border: 2px solid rgba(255, 255, 255, 0.1);
  background-color: var(--color-surface);
}

.founder-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.founder-content {
  text-align: center;
}

.founder-name {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--color-text);
}

.founder-role {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

.founder-bio {
  color: var(--color-text-muted);
  font-size: 1.1rem;
  line-height: 1.7;
  max-width: 450px;
  margin: 0 auto;
}

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all var(--transition-fast);
  color: var(--color-text);
  z-index: 10;
  backdrop-filter: blur(10px);
}

.carousel-btn:hover {
  background: rgba(0, 255, 157, 0.1);
  border-color: var(--color-primary);
  color: var(--color-primary);
  transform: translateY(-50%) scale(1.1);
}

.carousel-btn.prev {
  left: 0;
}

.carousel-btn.next {
  right: 0;
}

.carousel-dots {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-top: 3rem;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  border: none;
  cursor: pointer;
  transition: all var(--transition-fast);
  padding: 0;
}

.dot:hover {
  background: rgba(255, 255, 255, 0.4);
  transform: scale(1.2);
}

.dot.active {
  background: var(--color-primary);
  width: 30px;
  border-radius: 5px;
}

@media (max-width: 768px) {
  .carousel-track {
    max-width: 90%;
    height: 450px;
  }

  .founder-card {
    padding: 2rem 1.5rem;
    min-height: 400px;
  }

  .founder-name {
    font-size: 1.5rem;
  }

  .founder-bio {
    font-size: 1rem;
  }

  .carousel-btn {
    width: 40px;
    height: 40px;
  }

  .carousel-btn.prev {
    left: -10px;
  }

  .carousel-btn.next {
    right: -10px;
  }

  .founder-card-wrapper.side {
    display: none;
  }
}
</style>
