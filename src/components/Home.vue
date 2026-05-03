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

  <!-- Info Boxes Section -->
  <section class="info-boxes">
    <!-- Who We Are Box -->
    <div class="info-box who-we-are">
      <h3>WHO WE ARE</h3>
      <h4>INDUSTRIAL GRUNGE FROM VIAREGGIO</h4>
      <p>Saints & Bastards is an industrial grunge band born in Viareggio, Italy. We blend 90s rage and modern sound research with politically charged lyrics about climate, inequality, depression and social injustice. Duality. Truth. Action.</p>
      <a href="#" @click="$emit('navigate', 'band')" class="read-more">READ MORE</a>
    </div>

    <!-- Latest From The Lab Box -->
    <div class="info-box latest-lab">
      <h3>LATEST FROM THE LAB</h3>
      <div class="lab-content">
        <img src="/images/hero-left.jpg" alt="Latest Work" />
      </div>
      <p>WORKING ON OUR DEBUT ALBUM</p>
      <p class="small">STAY TUNED</p>
    </div>

    <!-- Upcoming Shows Box -->
    <div class="info-box upcoming-shows">
      <h3>UPCOMING SHOWS</h3>
      <div class="shows-list">
        <div class="show-item">
          <span class="date">01 <span class="month">MAY</span></span>
          <div class="show-details">
            <p>POOL JAZZ CLUB</p>
            <p>VIAREGGIO, ITALY</p>
            <p class="status sold-out">SOLD OUT</p>
          </div>
        </div>
        <div class="show-item">
          <span class="date">12 <span class="month">JUN</span></span>
          <div class="show-details">
            <p>TBA</p>
            <p>ITALY</p>
            <p class="status info-soon">INFO SOON</p>
          </div>
        </div>
        <div class="show-item">
          <span class="date">03 <span class="month">JUL</span></span>
          <div class="show-details">
            <p>TBA</p>
            <p>ITALY</p>
            <p class="status info-soon">INFO SOON</p>
          </div>
        </div>
      </div>
      <a href="#" @click="$emit('navigate', 'live')" class="view-all">VIEW ALL DATES</a>
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
  background: #000;
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
  background: linear-gradient(to bottom, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, 0) 20%);
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
  background: linear-gradient(to top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, 0) 40%);
  z-index: 2;
  pointer-events: none;
  mix-blend-mode: multiply;
}

.hero-content {
  position: absolute;
  bottom: 40px;
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
  font-size: clamp(1.1rem, 3.5vw, 2.2rem);
  font-family: 'Orbitron', sans-serif;
  font-weight: 700;
  margin: 0 0 0.2rem 0;
  letter-spacing: 3px;
  text-transform: uppercase;
}

.hero-content p {
  font-size: clamp(0.5rem, 1vw, 0.7rem);
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

/* Info Boxes Section */
.info-boxes {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  max-width: 1400px;
  margin: -35rem auto 4rem auto;
  padding: 4rem 2rem;
  background: #000;
  position: relative;
  z-index: 10;
}

.info-box {
  padding: 2rem;
  border-left: 3px solid;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  border-top: 1px solid rgba(255, 255, 255, 0.15);
  border-right: 1px solid rgba(255, 255, 255, 0.1);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.info-box h3 {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin: 0 0 0.5rem 0;
  opacity: 0.7;
}

.info-box h4 {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  letter-spacing: 1px;
  margin: 0 0 1.5rem 0;
  text-transform: uppercase;
}

.info-box p {
  font-size: 0.9rem;
  line-height: 1.6;
  margin: 0 0 1rem 0;
  opacity: 0.9;
}

.info-box .small {
  font-size: 0.8rem;
  opacity: 0.7;
}

/* Who We Are Box */
.who-we-are {
  border-left-color: #4a9eff;
}

.who-we-are h3,
.who-we-are h4 {
  color: #4a9eff;
}

.read-more {
  color: #4a9eff;
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 1px;
  transition: opacity 0.3s;
}

.read-more:hover {
  opacity: 0.7;
}

/* Latest From The Lab Box */
.latest-lab {
  border-left-color: #fff;
}

.latest-lab h3,
.latest-lab h4 {
  color: #fff;
}

.lab-content {
  width: 100%;
  height: 150px;
  margin-bottom: 1rem;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.lab-content img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Upcoming Shows Box */
.upcoming-shows {
  border-left-color: #ff6b35;
}

.upcoming-shows h3,
.upcoming-shows h4 {
  color: #ff6b35;
}

.shows-list {
  margin-bottom: 1.5rem;
}

.show-item {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.show-item:last-child {
  border-bottom: none;
  margin-bottom: 0;
  padding-bottom: 0;
}

.date {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.5rem;
  font-weight: 700;
  min-width: 50px;
  color: #ff6b35;
}

.date .month {
  display: block;
  font-size: 0.7rem;
  opacity: 0.8;
}

.show-details p {
  margin: 0 0 0.3rem 0;
  font-size: 0.85rem;
}

.show-details .status {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 1px;
  margin-top: 0.3rem;
}

.status.sold-out {
  color: #ff6b35;
}

.status.info-soon {
  color: #aaa;
}

.view-all {
  color: #ff6b35;
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 1px;
  transition: opacity 0.3s;
}

.view-all:hover {
  opacity: 0.7;
}

@media (max-width: 1024px) {
  .info-boxes {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}
</style>
