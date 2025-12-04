<script setup>
import { ref } from 'vue';

const formData = ref({
  fullName: '',
  email: '',
  company: '',
  role: '',
  goals: ''
});

const handleSubmit = () => {
  console.log('Form submitted:', formData.value);
};
</script>

<template>
  <section class="contact-section">
    <div class="container">
      <div class="header">
        <div class="badge">Comencemos ahora!</div>
        <h2>Preparado para <span class="highlight">Acelerar</span> tu crecimiento?</h2>
        <p class="subtitle">Comencemos con una conversación para entender tus metas y como podemos ayudarte a alcanzarlas</p>
      </div>

      <div class="content-grid">
        <!-- Left Column -->
        <div class="info-column">
          <div class="info-card">
            <h3>¿Qué esperar?</h3>
            <ul class="benefits-list">
              <li>
                <span class="icon">✓</span>
                Llamada de descubrimiento de 15 minutos para entender tus necesidades
              </li>
              <li>
                <span class="icon">✓</span>
                Recomendaciones de estrategia personalizadas
              </li>
              <li>
                <span class="icon">✓</span>
                Acceso a nuestro deck de agencia completo
              </li>
              <li>
                <span class="icon">✓</span>
                Sin compromisos u  obligaciones
              </li>
            </ul>
          </div>

          <div class="info-card small">
            <h3>¿Por qué comenzar con una conversación?</h3>
            <p>Cada partnership exitoso comienza con la comprensión. Queremos aprender sobre tus desafíos y metas únicas antes de compartir nuestras capacidades y estudios de caso.</p>
          </div>
        </div>

        <!-- Right Column (Form) -->
        <div class="form-column">
          <div class="form-card">
            <div class="form-header">
              <span class="calendar-icon">📅</span>
              <h3>Programar tu llamada</h3>
            </div>
            <p class="form-desc">Llenar el formulario a continuación y nos contactaremos en 24 horas</p>

            <form @submit.prevent="handleSubmit">
              <div class="form-row">
                <div class="form-group">
                  <label>Nombre completo *</label>
                  <input v-model="formData.fullName" type="text" placeholder="Tu nombre completo" required />
                </div>
                <div class="form-group">
                  <label>Correo electrónico *</label>
                  <input v-model="formData.email" type="email" placeholder="tu@empresa.com" required />
                </div>
              </div>

              <div class="form-group">
                <label>Empresa *</label>
                <input v-model="formData.company" type="text" placeholder="Nombre de tu empresa" required />
              </div>

              <div class="form-group">
                <label>Tu rol *</label>
                <select v-model="formData.role" required>
                  <option value="" disabled selected>Selecciona tu rol</option>
                  <option value="founder">Founder / CEO</option>
                  <option value="marketing">Marketing Director</option>
                  <option value="other">Otros</option>
                </select>
              </div>

              <div class="form-group">
                <label>¿Cuáles son tus metas (Opcional)</label>
                <textarea v-model="formData.goals" placeholder="¿Cuáles son tus principales desafíos o metas?" rows="4"></textarea>
              </div>

              <button type="submit" class="submit-btn">
                📅 Programar mi llamada
              </button>
              
              <p class="privacy-note">Respetamos tu privacidad y nunca te spamaremos.</p>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  background: 
    radial-gradient(circle at 50% 100%, rgba(0, 255, 157, 0.05) 0%, transparent 50%),
    linear-gradient(180deg, #111111 0%, #050505 100%);
  color: #ffffff;
  padding: 70px 20px;
  width: 100%;
  position: relative;
  overflow: hidden;
}

.contact-section::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 600px;
  height: 600px;
  background: var(--gradient-glow);
  filter: blur(100px);
  opacity: 0.2;
  pointer-events: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.header {
  text-align: center;
  margin-bottom: 60px;
}

.badge {
  display: inline-block;
  background: rgba(0, 255, 157, 0.1);
  color: var(--color-primary);
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 0.9rem;
  margin-bottom: 20px;
  border: 1px solid rgba(0, 255, 157, 0.2);
  box-shadow: 0 0 10px rgba(0, 255, 157, 0.1);
}

h2 {
  font-size: 2.75rem;
  font-weight: 700;
  margin-bottom: 16px;
}

.highlight {
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
  filter: drop-shadow(0 0 10px rgba(0, 255, 157, 0.3));
}

.subtitle {
  color: var(--color-text-muted);
  font-size: 1.1rem;
  max-width: 600px;
  margin: 0 auto;
}

.content-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: start;
}

/* Info Column */
.info-column {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.info-card {
  background: var(--glass-bg);
  border: var(--glass-border);
  border-radius: 16px;
  padding: 32px;
  transition: all var(--transition-fast);
  backdrop-filter: blur(10px);
}

.info-card:hover {
  border-color: rgba(0, 255, 157, 0.3);
  box-shadow: var(--shadow-glow);
  transform: translateY(-2px);
}

.info-card h3 {
  font-size: 1.25rem;
  margin-bottom: 24px;
  font-weight: 600;
}

.benefits-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.benefits-list li {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  color: #e5e7eb;
}

.icon {
  color: var(--color-primary);
  font-weight: bold;
  text-shadow: 0 0 5px rgba(0, 255, 157, 0.5);
}

.info-card.small p {
  color: var(--color-text-muted);
  line-height: 1.6;
  font-size: 0.95rem;
}

/* Form Column */
.form-card {
  background: var(--glass-bg);
  border: var(--glass-border);
  border-radius: 16px;
  padding: 35px;
  backdrop-filter: blur(10px);
  transition: all var(--transition-fast);
  box-shadow: var(--shadow-card);
}

.form-card:hover {
  border-color: rgba(0, 255, 157, 0.2);
  box-shadow: 0 12px 32px rgba(0, 255, 157, 0.15);
}

.form-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 8px;
}

.calendar-icon {
  font-size: 1.5rem;
  color: var(--color-primary);
  filter: drop-shadow(0 0 5px rgba(0, 255, 157, 0.4));
}

.form-desc {
  color: var(--color-text-muted);
  margin-bottom: 32px;
  font-size: 0.95rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

label {
  font-size: 0.9rem;
  font-weight: 500;
  color: #e5e7eb;
}

input, select, textarea {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 12px 16px;
  color: white;
  font-size: 0.95rem;
  width: 100%;
  transition: all var(--transition-fast);
}

input:focus, select:focus, textarea:focus {
  outline: none;
  border-color: var(--color-primary);
  background: rgba(0, 255, 157, 0.05);
  box-shadow: 0 0 0 3px rgba(0, 255, 157, 0.1);
}

input::placeholder, textarea::placeholder {
  color: rgba(255, 255, 255, 0.3);
}

.submit-btn {
  width: 100%;
  background: var(--gradient-primary);
  color: #0d0d0d;
  border: none;
  border-radius: 8px;
  padding: 14px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-fast);
  margin-top: 12px;
  box-shadow: 0 4px 15px rgba(0, 255, 157, 0.3);
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 255, 157, 0.4);
}

.submit-btn:active {
  transform: translateY(0);
}

.privacy-note {
  text-align: center;
  color: #6b7280;
  font-size: 0.8rem;
  margin-top: 16px;
}

@media (max-width: 768px) {
  .content-grid {
    grid-template-columns: 1fr;
  }
  
  .form-row {
    grid-template-columns: 1fr;
  }
  
  h2 {
    font-size: 2rem;
  }
}
</style>
