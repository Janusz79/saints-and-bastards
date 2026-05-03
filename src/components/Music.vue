<template>
  <section class="music">
    <h2>La Nostra Musica</h2>
    <div class="tracks">
      <div v-for="track in tracks" :key="track.id" class="track-card">
        <h3>{{ track.title }}</h3>
        <p>Album: <strong>{{ track.album }}</strong></p>
        <p>{{ track.year }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const tracks = ref([
  { id: 1, title: 'Wild Hearts', album: 'Rebellion', year: 2025 },
  { id: 2, title: 'Broken Dreams', album: 'Rebellion', year: 2025 },
  { id: 3, title: 'Midnight Thunder', album: 'Electric Nights', year: 2024 },
])
</script>

<style scoped>
.music {
  padding: 2rem 0;
}

.music h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: #ff6b6b;
  text-transform: uppercase;
}

.tracks {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.track-card {
  background: rgba(255, 255, 255, 0.1);
  padding: 1.5rem;
  border: 1px solid #ff6b6b;
  border-radius: 5px;
  transition: transform 0.3s;
}

.track-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 107, 107, 0.1);
}

.track-card h3 {
  color: #ff6b6b;
  margin-bottom: 0.5rem;
}

.track-card p {
  color: #aaa;
}
</style>
