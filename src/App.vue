<template>
  <div class="container">
    <header>
      <div class="logo">
        <h1>SAINTS & BASTARDS</h1>
        <p>Rock Band</p>
      </div>
      <nav>
        <a href="#home" @click="currentPage = 'home'">Home</a>
        <a href="#music" @click="currentPage = 'music'">Musica</a>
        <a href="#tour" @click="currentPage = 'tour'">Tour</a>
        <a href="#contact" @click="currentPage = 'contact'">Contatti</a>
      </nav>
    </header>

    <main>
      <Home v-if="currentPage === 'home'" />
      <Music v-if="currentPage === 'music'" />
      <Tour v-if="currentPage === 'tour'" />
      <Contact v-if="currentPage === 'contact'" />
    </main>

    <footer>
      <p>&copy; 2026 Saints and Bastards. Tutti i diritti riservati.</p>
      <div class="social">
        <a href="#" target="_blank">Facebook</a>
        <a href="#" target="_blank">Instagram</a>
        <a href="#" target="_blank">YouTube</a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Home from './components/Home.vue'
import Music from './components/Music.vue'
import Tour from './components/Tour.vue'
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
