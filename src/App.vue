<template>
  <div class="container">
    <header>
      <!-- Social Media Top Right -->
      <div class="social-top">
        <a href="https://instagram.com" target="_blank" title="Instagram">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <circle cx="12" cy="12" r="11"/>
            <circle cx="12" cy="12" r="8" fill="#1a1a1a"/>
            <circle cx="12" cy="12" r="3"/>
            <circle cx="18" cy="6" r="1"/>
          </svg>
        </a>
        <a href="https://youtube.com" target="_blank" title="YouTube">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l5-3-5-3v6z"/>
          </svg>
        </a>
        <a href="https://facebook.com" target="_blank" title="Facebook">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <circle cx="12" cy="12" r="10"/>
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm3 11h-2v7h-3v-7H9v-3h1V7c0-1.1.9-2 2-2h2v3h-1v2h1v3z" fill="#1a1a1a"/>
          </svg>
        </a>
        <a href="https://spotify.com" target="_blank" title="Spotify">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <circle cx="12" cy="12" r="10"/>
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.35 14.35c-.35.35-.9.35-1.25 0-1.95-1.2-4.4-1.85-6.85-1.85-1.05 0-2.1.15-3.1.4.35 0 .7.05 1.05.05 2.1 0 4.05-.65 5.7-1.85.35-.3.35-.85 0-1.2-.3-.3-.85-.3-1.15 0-1.35.95-2.9 1.5-4.55 1.5-.35 0-.7-.05-1.05-.1v1.65c1.5.8 3.2 1.3 5 1.3 2.25 0 4.35-.65 6.15-1.8.35-.25.85-.15 1.1.15.25.35.15.9-.2 1.15z" fill="#1a1a1a"/>
          </svg>
        </a>
      </div>

      <!-- Main Header Navigation -->
      <div class="nav-wrapper">
        <!-- Left Navigation -->
        <nav class="nav-left">
          <a href="#home" @click="currentPage = 'home'">HOME</a>
          <a href="#band" @click="currentPage = 'band'">BAND</a>
          <a href="#music" @click="currentPage = 'music'">MUSIC</a>
        </nav>

        <!-- Center Logo -->
        <div class="logo">
          <h1>SAINTS & BASTARDS</h1>
        </div>

        <!-- Right Navigation -->
        <nav class="nav-right">
          <a href="#live" @click="currentPage = 'live'">LIVE</a>
          <a href="#media" @click="currentPage = 'media'">MEDIA</a>
          <a href="#contact" @click="currentPage = 'contact'">CONTACT</a>
        </nav>
      </div>
    </header>

    <main>
      <Home v-if="currentPage === 'home'" />
      <Band v-if="currentPage === 'band'" />
      <Music v-if="currentPage === 'music'" />
      <Live v-if="currentPage === 'live'" />
      <Media v-if="currentPage === 'media'" />
      <Contact v-if="currentPage === 'contact'" />
    </main>

    <footer>
      <p>&copy; 2026 Saints and Bastards. Tutti i diritti riservati.</p>
      <div class="footer-links">
        <a href="#sitemap">Sitemap</a>
        <a href="#privacy">Privacy</a>
        <a href="#terms">Terms</a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Home from './components/Home.vue'
import Band from './components/Band.vue'
import Music from './components/Music.vue'
import Live from './components/Live.vue'
import Media from './components/Media.vue'
import Contact from './components/Contact.vue'

const currentPage = ref('home')
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  background: transparent;
  backdrop-filter: blur(10px);
  padding: 1rem 2rem;
  border: none;
  position: relative;
  z-index: 100;
}

.social-top {
  position: absolute;
  top: 1.5rem;
  right: 2rem;
  display: flex;
  gap: 1.5rem;
}

.social-top a {
  flex-shrink: 0;
}

.social-top a:hover {
  color: #ff6b6b;
}

.social-top svg {
  width: 20px;
  height: 20px;
  display: block;
  flex-shrink: 06b;
}

.social-top svg {
  width: 22px;
  height: 22px;
}

.nav-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 3rem;
  max-width: 1400px;
  margin: 0 auto;
  padding-top: 1rem;
}

.nav-left,
.nav-right {
  display: flex;
  gap: 2.5rem;
  flex: 1;
}

.nav-right {
  justify-content: flex-end;
}

.nav-left a,
.nav-right a {
  color: #fff;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  transition: color 0.3s;
  cursor: pointer;
  position: relative;
}

.nav-left a:hover,
.nav-right a:hover {
  color: #ff6b6b;
}

.nav-left a::after,
.nav-right a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: #ff6b6b;
  transition: width 0.3s;
}

.nav-left a:hover::after,
.nav-right a:hover::after {
  width: 100%;
}

.logo {
  flex: 0 0 auto;
  text-align: center;
}

.logo h1 {
  font-size: 1.8rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 3px;
  color: #fff;
  margin: 0;
  text-shadow: 0 2px 10px rgba(255, 107, 107, 0.3);
}

main {
  flex: 1;
  padding: 2rem;
}

footer {
  background: rgba(0, 0, 0, 0.95);
  padding: 2rem;
  text-align: center;
  border-top: 1px solid rgba(255, 107, 107, 0.2);
  margin-top: 2rem;
}

footer p {
  margin: 0;
  color: #aaa;
  font-size: 0.9rem;
}

.footer-links {
  margin-top: 1rem;
  display: flex;
  gap: 2rem;
  justify-content: center;
}

.footer-links a {
  color: #ff6b6b;
  text-decoration: none;
  font-size: 0.85rem;
  transition: color 0.3s;
}

.footer-links a:hover {
  color: #fff;
}

@media (max-width: 768px) {
  .nav-wrapper {
    flex-wrap: wrap;
    gap: 1rem;
  }

  .nav-left,
  .nav-right {
    flex: 1;
    gap: 1rem;
    font-size: 0.8rem;
  }

  .logo h1 {
    font-size: 1.2rem;
    letter-spacing: 1px;
  }

  .social-top {
    top: 0.5rem;
    right: 1rem;
    gap: 1rem;
  }

  .social-top svg {
    width: 18px;
    height: 18px;
  }
}
</style>
