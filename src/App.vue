<template>
  <div class="container">
    <header>
      <!-- Social Media Top Right -->
      <div class="social-top">
        <a href="https://instagram.com" target="_blank" title="Instagram">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.6 0 12 0zm0 22.5c-5.79 0-10.5-4.71-10.5-10.5S6.21 1.5 12 1.5s10.5 4.71 10.5 10.5-4.71 10.5-10.5 10.5z"/>
          </svg>
        </a>
        <a href="https://youtube.com" target="_blank" title="YouTube">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
          </svg>
        </a>
        <a href="https://facebook.com" target="_blank" title="Facebook">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
          </svg>
        </a>
        <a href="https://spotify.com" target="_blank" title="Spotify">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.6 0 12 0zm5.6 17.3c-.3.5-.9.7-1.4.4-3.8-2.3-8.6-2.8-14.3-1.5-.6.1-1.2-.3-1.3-.9-.1-.6.3-1.2.9-1.3 6.3-1.5 11.6-.9 15.9 1.8.5.3.7.9.4 1.4zm1.5-3.3c-.4.6-1.1.8-1.7.4-4.3-2.7-10.9-3.5-16.1-1.9-.6.2-1.3-.1-1.5-.7-.2-.6.1-1.3.7-1.5 5.8-1.8 13-1 17.9 2.2.6.4.8 1.1.4 1.7zm.1-3.5c-5.1-3.1-13.5-3.4-18.4-1.9-.7.2-1.4-.2-1.6-.9-.2-.7.2-1.4.9-1.6 5.5-1.7 14.6-1.4 20.2 2.2.6.4 1 1.1.6 1.7-.4.6-1.1.9-1.7.5z"/>
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
  background: rgba(0, 0, 0, 0.8);
  padding: 2rem;
  border-bottom: 3px solid #ff6b6b;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo h1 {
  font-size: 2rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.logo p {
  font-size: 0.9rem;
  color: #ff6b6b;
  margin-top: 0.5rem;
}

nav {
  display: flex;
  gap: 2rem;
}

nav a {
  color: #fff;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
  cursor: pointer;
}

nav a:hover {
  color: #ff6b6b;
}

main {
  flex: 1;
  padding: 2rem;
}

footer {
  background: rgba(0, 0, 0, 0.9);
  padding: 2rem;
  text-align: center;
  border-top: 3px solid #ff6b6b;
  margin-top: 2rem;
}

.social {
  margin-top: 1rem;
  display: flex;
  gap: 1.5rem;
  justify-content: center;
}

.social a {
  color: #ff6b6b;
  text-decoration: none;
  transition: color 0.3s;
}

.social a:hover {
  color: #fff;
}
</style>
