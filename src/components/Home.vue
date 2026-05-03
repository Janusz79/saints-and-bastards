<template>
  <section class="hero-container">
    <!-- Hero Reveal Slider -->
    <div 
      class="hero-reveal" 
      ref="revealContainer"
      @mousedown="startDrag"
      @touchstart="startDrag"
    >
      <!-- Right Image (background) -->
      <div class="hero-image hero-right">
        <img src="/images/hero-right.jpg" alt="Hero Right" />
      </div>

      <!-- Left Image (clip) -->
      <div class="hero-image hero-left" :style="{ clipPath: `polygon(0 0, ${revealPosition}% 0, ${revealPosition}% 100%, 0 100%)` }">
        <img src="/images/hero-left.jpg" alt="Hero Left" />
      </div>

      <!-- Gradient Overlay (top to bottom, black to transparent) -->
      <div class="hero-gradient-overlay"></div>

      <!-- Gradient Overlay (bottom to top, black to transparent) -->
      <div class="hero-gradient-overlay-bottom"></div>

      <!-- Hero Text Overlay -->
      <div class="hero-content">
        <div class="hero-text">
          <h2>SAINTS & BASTARDS</h2>
          <p>EVERY SAINT HAS A BASTARD SIDE</p>
        </div>
        
        <div class="hero-buttons">
          <button class="cta-button">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <circle cx="12" cy="12" r="10"/>
              <path d="M8 5.14v13.72c0 .6.64.94 1.14.59l11.07-6.86c.5-.31.5-1.09 0-1.4L9.14 4.55C8.64 4.2 8 4.54 8 5.14Z" fill="black"/>
            </svg>
            LISTEN
          </button>
          <button class="cta-button">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M23 7l-7 5 7 5V7z"/>
              <rect x="1" y="5" width="15" height="14" rx="2" ry="2"/>
            </svg>
            WATCH
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const revealContainer = ref(null)
const revealPosition = ref(50)
const isDragging = ref(false)
const targetPosition = ref(50)

const startDrag = (e) => {
  isDragging.value = true
  document.addEventListener('mousemove', onDrag)
  document.addEventListener('mouseup', stopDrag)
  document.addEventListener('touchmove', onDrag)
  document.addEventListener('touchend', stopDrag)
}

const onDrag = (e) => {
  if (!isDragging.value || !revealContainer.value) return

  const rect = revealContainer.value.getBoundingClientRect()
  const clientX = e.touches ? e.touches[0].clientX : e.clientX
  const x = clientX - rect.left
  const percent = Math.max(0, Math.min(100, (x / rect.width) * 100))
  
  revealPosition.value = percent
}

const stopDrag = () => {
  isDragging.value = false
  targetPosition.value = 50
  
  // Smooth animation back to center
  const animate = () => {
    const diff = targetPosition.value - revealPosition.value
    if (Math.abs(diff) > 0.1) {
      revealPosition.value += diff * 0.1
      requestAnimationFrame(animate)
    } else {
      revealPosition.value = 50
    }
  }
  
  animate()
  
  document.removeEventListener('mousemove', onDrag)
  document.removeEventListener('mouseup', stopDrag)
  document.removeEventListener('touchmove', onDrag)
  document.removeEventListener('touchend', stopDrag)
}
</script>

<style scoped>
.hero-container {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #1a1a1a;
  margin: 0;
  padding: 0;
}

.hero-reveal {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: grab;
}

.hero-reveal:active {
  cursor: grabbing;
}

.hero-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
}

.hero-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  pointer-events: none;
  -webkit-user-drag: none;
}

.hero-right {
  z-index: 1;
}

.hero-left {
  z-index: 2;
  transition: clip-path 0.05s linear;
}

.hero-gradient-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0));
  z-index: 2;
  pointer-events: none;
  mix-blend-mode: multiply;
}

.hero-gradient-overlay-bottom {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0));
  z-index: 2;
  pointer-events: none;
  mix-blend-mode: multiply;
}

.hero-content {
  position: absolute;
  bottom: 60px;
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
  z-index: 4;
  color: white;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.7);
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  pointer-events: none;
}

.hero-text {
  margin-bottom: 2rem;
  pointer-events: none;
}

.hero-content h2 {
  font-size: clamp(1.5rem, 5vw, 3rem);
  font-family: 'Orbitron', sans-serif;
  font-weight: 700;
  margin: 0 0 0.3rem 0;
  letter-spacing: 3px;
  text-transform: uppercase;
}

.hero-content p {
  font-size: clamp(0.6rem, 1.5vw, 0.9rem);
  margin: 0;
  font-weight: 300;
  letter-spacing: 2px;
}

.cta-button {
  padding: 12px 30px;
  background: rgba(255, 255, 255, 0.1);
  color: white;
  border: 2px solid white;
  border-radius: 0;
  font-family: 'Orbitron', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 2px;
  cursor: pointer;
  transition: all 0.3s;
  text-transform: uppercase;
  pointer-events: auto;
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 0 10px;
}

.cta-button svg {
  width: 20px;
  height: 20px;
}

.cta-button:hover {
  background: white;
  color: #1a1a1a;
  transform: scale(1.05);
}

.hero-buttons {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0;
  pointer-events: auto;
}

@media (max-width: 768px) {
  .hero-content {
    padding: 0 20px;
  }

  .reveal-handle {
    width: 40px;
    height: 40px;
  }
}
</style>
