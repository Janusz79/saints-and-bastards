<template>
  <div class="container">
    <header>


      <!-- Main Header Navigation -->
      <div class="nav-wrapper">
        <!-- Left Navigation -->
        <nav class="nav-left">
          <a href="#home" @click="currentPage = 'home'">HOME</a>
          <a href="#band" @click="currentPage = 'band'">BAND</a>
          <a href="#music" @click="currentPage = 'music'">MUSIC</a>
        </nav>

        <!-- Center Logo -->
        <div class="logo" @click="mobileMenuOpen = !mobileMenuOpen">
          <img src="/images/LogoSaintsAndBastards.svg" alt="Saints and Bastards" class="band-logo" />
        </div>

        <!-- Right Navigation -->
        <nav class="nav-right">
          <a href="#live" @click="currentPage = 'live'">LIVE</a>
          <a href="#media" @click="currentPage = 'media'">MEDIA</a>
          <a href="#contact" @click="currentPage = 'contact'">CONTACT</a>
        </nav>
      </div>

      <!-- Mobile Menu Drawer -->
      <nav class="mobile-menu" :class="{ open: mobileMenuOpen }">
        <div class="mobile-menu-links" >
          <a href="#home" @click="currentPage = 'home'; mobileMenuOpen = false">HOME</a>
          <a href="#band" @click="currentPage = 'band'; mobileMenuOpen = false">BAND</a>
          <a href="#music" @click="currentPage = 'music'; mobileMenuOpen = false">MUSIC</a>
          <a href="#live" @click="currentPage = 'live'; mobileMenuOpen = false">LIVE</a>
          <a href="#media" @click="currentPage = 'media'; mobileMenuOpen = false">MEDIA</a>
          <a href="#contact" @click="currentPage = 'contact'; mobileMenuOpen = false">CONTACT</a>
          <div class="mobile-menu-logo" @click="mobileMenuOpen = !mobileMenuOpen">
            <img src="/images/LogoSaintsAndBastards.svg" alt="Saints and Bastards" class="band-logo" />
          </div>
        </div>
      </nav>
    </header>

    <main>
      <Home v-if="currentPage === 'home'" @navigate="currentPage = $event" />
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
const mobileMenuOpen = ref(false)
</script>

<style scoped>

.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
   background: black !important;
}

header {
  background: transparent;
  background: linear-gradient();
  padding: 1rem 2rem;
  border: none;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 100;
}

.social-top {
  position: absolute;
  top: 1.5rem;
  right: 2rem;
  display: flex;
  gap: 1.5rem;
  z-index: 201;
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
  display: flex;
  align-items: center;
  justify-content: center;
}

.band-logo {
  height: 90px;
  width: auto;
  opacity: 0.95;
  transition: opacity 0.3s;
  filter: brightness(0) invert(1);
}

.band-logo:hover {
  opacity: 1;
}

.logo h1 {
  font-size: 1rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 3px;
  color: #fff;
  margin: 0;
  text-shadow: 0 2px 10px rgba(255, 107, 107, 0.3);
}

main {
  flex: 1;
  padding: 0;
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

/* Mobile Menu */
.mobile-menu {
  display: none;
  position: fixed;
  top: calc(-100% - -250px);
  left: 0;
  right: 0;
  width: 100%;
  flex-direction: column;
  gap: 0;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  transition: top 0.3s ease;
  z-index: 200;
}

.mobile-menu-links {
  position: relative;
  flex: 1;
  display: flex;
  flex-direction: column;
  
}

.mobile-menu.open {
  top: 0;
}

.mobile-menu-logo {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 2rem;
  background: rgba(0, 0, 0, 0.95);
  border-radius:0 0 130px 130px ;
  cursor: pointer;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  width: 100px;
  margin: auto;
}

.mobile-menu-logo h1 {
  display: none;
}

.mobile-menu-logo .band-logo {
  height: 70px;
  width: 70px;
  opacity: 0.95;
  transition: opacity 0.3s;
}

.mobile-menu-logo:active .band-logo {
  opacity: 1;
}

.mobile-menu a {
background: rgba(0, 0, 0, 0.95);
  padding: 1rem 2rem;
  color: #fff;
  text-decoration: none;
  font-family: 'Orbitron', sans-serif;
  text-align: center;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  border: 1px solid rgba(0,0,0, 1);
  margin-top: -1px;
  transition: background 0.3s;
  cursor: pointer;
}

.mobile-menu a:hover {
  background: rgba(255, 255, 255, 0.1);
}

@media (max-width: 768px) {
  .nav-wrapper {
    flex-wrap: wrap;
    gap: 1rem;
  }

  .nav-left,
  .nav-right {
    display: none;
  }

  .logo {
    display: none;
  }

  .mobile-menu {
    display: flex;
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
