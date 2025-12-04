<script setup>
import { ref } from 'vue';
import BaseCard from '@/shared/components/ui/BaseCard.vue';

const founders = [
  {
    id: 1,
    name: 'Francisco Hurtado',
    role: 'Co-Fundador',
    image: 'https://i.postimg.cc/W3hgn10M/1755026008117.jpg',
    bio: 'Ingeniero de software apasionado por las redes sociales, con experiencia en la industria del streaming y plataformas digitales.',
    socials: {
      linkedin: 'https://www.linkedin.com/in/francisco-hurtado-p-0b9602301/',
      instagram: 'https://www.instagram.com/franmanic/',
      email: 'fleemocontacto@gmail.com'
    }
  },
  {
    id: 2,
    name: 'Arturo Reyes',
    role: 'Co-Fundador',
    image: 'https://i.postimg.cc/YSNsH8P3/1720583786545.jpg',
    bio: 'Fotógrafo con amplia experiencia en producción audiovisual y publicidad.',
    socials: {
      linkedin: 'https://www.linkedin.com/in/arturo-reyes-298a17318/',
      instagram: 'https://www.instagram.com/arturoreyesfoto/',
      email: 'fleemocontacto@gmail.com'
    }
  },
  {
    id: 3,
    name: 'Andre Valdivieso',
    role: 'Socio Estrategico',
    image: 'https://i.postimg.cc/wM127kW6/1749573185395.jpg',
    bio: 'Estudiante de administración y marketing, apasionado por el marketing digital y el crecimiento en redes sociales.',
    socials: {
      linkedin: 'https://www.linkedin.com/in/andre-valdivieso-sanchez-a334202a8/',
      instagram: 'https://www.instagram.com/andre_valdivieso12/',
      email: 'fleemocontacto@gmail.com'
    }
  },
  {
    id: 4,
    name: 'ElVento',
    role: 'Socio Estrategico',
    image: 'https://i.postimg.cc/GhhbyHYJ/channels4-profile.jpg',
    bio: 'Creador de contenido con sólido conocimiento del funcionamiento y estrategias en redes sociales.',
    socials: {
      tiktok: 'https://www.tiktok.com/@elvento1',
      instagram: 'https://www.instagram.com/iam_vent1/',
      email: 'fleemocontacto@gmail.com'
    }
  },
  {
    id: 5,
    name: 'Sebastian Quinde',
    role: 'Socio Estrategico',
    image: 'https://i.postimg.cc/CLYgVdJW/Imagen-de-Whats-App-2025-11-26-a-las-12-22-19-e3d50a7f.jpg',
    bio: 'Ingeniero de software enfocado en el desarrollo de soluciones tecnológicas modernas.',
    socials: {
      linkedin: 'https://www.linkedin.com/in/sebastian-quinde-oblitas-51142b285/',
      instagram: 'https://www.instagram.com/sebastian.quinde11/',
      email: 'fleemocontacto@gmail.com'
    }
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
                
                <!-- Social Media Buttons -->
                <div class="social-links">
                  <a 
                    v-if="founder.socials.linkedin" 
                    :href="founder.socials.linkedin" 
                    class="social-btn"
                    aria-label="LinkedIn"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                    </svg>
                  </a>
                  
                  <a 
                    v-if="founder.socials.twitter" 
                    :href="founder.socials.twitter" 
                    class="social-btn"
                    aria-label="Twitter/X"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
                    </svg>
                  </a>
                  
                  <a 
                    v-if="founder.socials.instagram" 
                    :href="founder.socials.instagram" 
                    class="social-btn"
                    aria-label="Instagram"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                    </svg>
                  </a>

                  <a 
                    v-if="founder.socials.tiktok" 
                    :href="founder.socials.tiktok" 
                    class="social-btn"
                    aria-label="tiktok"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M16.6 5.82s.51.5 0 0A4.28 4.28 0 0 1 15.54 3h-3.09v12.4a2.59 2.59 0 0 1-2.59 2.5c-1.42 0-2.6-1.16-2.6-2.6c0-1.72 1.66-3.01 3.37-2.48V9.66c-3.45-.46-6.47 2.22-6.47 5.64c0 3.33 2.76 5.7 5.69 5.7c3.14 0 5.69-2.55 5.69-5.7V9.01a7.35 7.35 0 0 0 4.3 1.38V7.3s-1.88.09-3.24-1.48"/>
                    </svg>
                  </a>
                  
                  <a 
                    v-if="founder.socials.email" 
                    :href="`mailto:${founder.socials.email}`" 
                    class="social-btn"
                    aria-label="Email"
                  >
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                      <polyline points="22,6 12,13 2,6"></polyline>
                    </svg>
                  </a>
                </div>
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
  padding: 80px 0;
  background: 
    radial-gradient(circle at 50% 50%, rgba(20, 20, 20, 1) 0%, rgba(10, 10, 10, 1) 100%),
    linear-gradient(0deg, #0a0a0a 0%, #141414 100%);
  overflow: hidden;
  position: relative;
}

.founders::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
}

.section-header {
  text-align: center;
  margin-bottom: 3.5rem;
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
  padding: 4rem 0;
  min-height: 525px;
}

.carousel-track {
  position: relative;
  width: 100%;
  max-width: 600px;
  height: 475px;
  display: flex;
  align-items: center;
  justify-content: center;
  perspective: 1000px;
}

.founder-card-wrapper {
  position: absolute;
  width: 100%;
  max-width: 400px;
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
  transform-style: preserve-3d;
}

.founder-card-wrapper.hidden {
  pointer-events: none;
}

.founder-card {
  background: linear-gradient(135deg, rgba(80, 77, 82, 0.15) 0%, rgba(208, 207, 209, 0.15) 100%);
  border: 1px solid rgba(83, 78, 88, 0.3);
  padding: 2.25rem 1.75rem;
  min-height: 510px;
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
  width: 260px;
  height: 270px;
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
  max-width: 100%;
  margin: 0 auto 1.5rem;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-top: 1.5rem;
}

.social-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--color-text-muted);
  transition: all var(--transition-fast);
  text-decoration: none;
  backdrop-filter: blur(10px);
}

.social-btn:hover {
  background: rgba(0, 255, 157, 0.1);
  border-color: var(--color-primary);
  color: var(--color-primary);
  transform: translateY(-3px) scale(1.1);
  box-shadow: 0 8px 20px rgba(0, 255, 157, 0.2);
}

.social-btn svg {
  transition: transform var(--transition-fast);
}

.social-btn:hover svg {
  transform: scale(1.1);
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
