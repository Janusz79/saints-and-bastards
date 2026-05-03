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
          <img src="/images/LogoNav.webp" alt="Saints and Bastards" class="band-logo" />
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
            <img src="/images/LogoNav.webp" alt="Saints and Bastards" class="band-logo" />
          </div>
        </div>
      </nav>
    </header>

    <main :class="`page-${currentPage}`">
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
      <div class="footer-social">
        <a :href="socialLinks.facebook" target="_blank" rel="noopener noreferrer" title="Facebook">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
          </svg>
        </a>
        <a :href="socialLinks.instagram" target="_blank" rel="noopener noreferrer" title="Instagram">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 0C8.74 0 8.333.015 7.053.072 5.775.132 4.905.333 4.217.63c-.68.264-1.277.623-1.834 1.18-.557.557-.916 1.154-1.18 1.834-.297.688-.498 1.558-.557 2.836C.015 8.333 0 8.74 0 12s.015 3.667.072 4.947c.06 1.277.261 2.148.558 2.836.264.68.623 1.277 1.18 1.834.557.557 1.154.916 1.834 1.18.688.297 1.559.498 2.837.557C8.333 23.985 8.74 24 12 24s3.667-.015 4.947-.072c1.280-.06 2.148-.261 2.836-.558.68-.264 1.277-.623 1.834-1.18.557-.557.916-1.154 1.18-1.834.297-.688.498-1.559.557-2.837.06-1.28.072-1.687.072-4.947s-.015-3.667-.072-4.947c-.06-1.277-.261-2.148-.558-2.836-.264-.68-.623-1.277-1.18-1.834-.557-.557-1.154-.916-1.834-1.18-.688-.297-1.559-.498-2.837-.557C15.667.015 15.26 0 12 0zm0 2.16c3.203 0 3.585.009 4.849.070 1.171.053 1.805.248 2.227.415.562.217.96.477 1.382.896.419.42.679.819.896 1.381.164.422.36 1.056.413 2.227.061 1.264.07 1.646.07 4.849s-.009 3.585-.07 4.849c-.053 1.171-.248 1.805-.415 2.227-.217.562-.477.96-.896 1.382-.42.419-.819.679-1.381.896-.422.164-1.056.36-2.227.413-1.264.061-1.646.07-4.849.07s-3.585-.009-4.849-.07c-1.171-.053-1.805-.248-2.227-.415-.562-.217-.96-.477-1.382-.896-.419-.42-.679-.819-.896-1.381-.164-.422-.36-1.056-.413-2.227-.061-1.264-.07-1.646-.07-4.849s.009-3.585.07-4.849c.053-1.171.248-1.805.415-2.227.217-.562.477-.96.896-1.382.42-.419.819-.679 1.381-.896.422-.164 1.056-.36 2.227-.413 1.264-.061 1.646-.07 4.849-.07z"/>
            <circle cx="12" cy="12" r="3.6"/>
          </svg>
        </a>
        <a :href="socialLinks.youtube" target="_blank" rel="noopener noreferrer" title="YouTube">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
          </svg>
        </a>
        <a :href="socialLinks.soundcloud" target="_blank" rel="noopener noreferrer" title="SoundCloud">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M7.3 6.65c-.4 0-.8.3-.8.75v9.1c0 .4.4.75.8.75.4 0 .8-.35.8-.75v-9.1c0-.45-.4-.75-.8-.75zm-2.1 1.85c-.4 0-.7.3-.7.65v7.2c0 .35.3.65.7.65.4 0 .7-.3.7-.65v-7.2c0-.35-.3-.65-.7-.65zm4.2-2.15c-.4 0-.8.3-.8.8v9.6c0 .4.4.8.8.8.4 0 .8-.4.8-.8V6.35c0-.5-.4-.8-.8-.8zm2.1 1.1c-.4 0-.8.35-.8.75v8.35c0 .4.4.75.8.75.4 0 .8-.35.8-.75V7.5c0-.4-.4-.75-.8-.75zm2.1-1.85c-.5 0-.9.3-.9.8v11c0 .5.4.9.9.9.5 0 .9-.4.9-.9v-11c0-.5-.4-.8-.9-.8zm2.1 1.25c-.4 0-.7.35-.7.75v8.8c0 .4.3.75.7.75s.7-.35.7-.75v-8.8c0-.4-.3-.75-.7-.75zm2.1-1.5c-.4 0-.8.3-.8.75v11.05c0 .4.4.75.8.75.4 0 .8-.35.8-.75V6.35c0-.45-.4-.75-.8-.75z"/>
          </svg>
        </a>
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

const socialLinks = {
  facebook: 'https://www.facebook.com/profile.php?id=61588887734829',
  instagram: 'https://www.instagram.com/saintsandbastards/',
  youtube: 'https://www.youtube.com/@SaintsAndBastards',
  soundcloud: 'https://soundcloud.com/saintsandbastards'
}
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
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.95) 0%, rgba(0, 0, 0, 0) 100%);
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
  background: #000;
}

/* Page-specific backgrounds */
main.page-home {
  background: #000;
}

main.page-band {
  background: linear-gradient(135deg, rgba(139, 0, 0, 0.3), rgba(255, 107, 107, 0.2)), #000;
}

main.page-music {
  background: linear-gradient(135deg, rgba(0, 50, 100, 0.3), rgba(100, 150, 255, 0.2)), #000;
}

main.page-live {
  background: linear-gradient(135deg, rgba(100, 0, 100, 0.3), rgba(200, 100, 255, 0.2)), #000;
}

main.page-media {
  background: linear-gradient(135deg, rgba(100, 100, 0, 0.3), rgba(255, 255, 100, 0.2)), #000;
}

main.page-contact {
  background: linear-gradient(135deg, rgba(0, 100, 100, 0.3), rgba(100, 255, 255, 0.2)), #000;
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

.footer-social {
  margin-top: 1.5rem;
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 107, 107, 0.2);
}

.footer-social a {
  color: #ff6b6b;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer-social a svg {
  width: 24px;
  height: 24px;
}

.footer-social a:hover {
  color: #fff;
  transform: scale(1.2);
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
