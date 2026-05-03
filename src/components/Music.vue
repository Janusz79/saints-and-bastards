<template>
  <section class="music">
    <h2>La Nostra Musica</h2>
    <div class="tracks">
      <div v-for="track in tracks" :key="track.id" class="track-card">
        <h3>{{ track.title }}</h3>
        <p class="role">{{ track.role }}</p>
        <audio controls class="audio-player">
          <source :src="track.audio" type="audio/mpeg">
          Your browser does not support the audio tag.
        </audio>
        <p class="meta">{{ track.year }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const tracks = ref([
  { id: 1, title: 'Alaskarma', role: 'Experimental', audio: '/Audio/Alaskarma Edit 2 Exp_auto_16bit_44hz_target-10.mp3', year: 2025 },
  { id: 2, title: 'No One', role: 'Single', audio: '/Audio/No one.mp3', year: 2025 },
  { id: 3, title: 'Passive Aggressive', role: 'Alternative', audio: '/Audio/Passive Aggressive E_auto_16bit_44hz_target-10.mp3', year: 2024 },
  { id: 4, title: 'Suoneria Bastardi', role: 'Interlude', audio: '/Audio/suoneriaBastardi.mp3', year: 2025 },
])
</script>

<style scoped>
.music {
  padding: 2rem 0;
  margin-top: 120px;
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
  margin: 0.5rem 0;
}

.role {
  color: #ff6b6b;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
}

.audio-player {
  width: 100%;
  margin: 1rem 0;
  height: 32px;
}

.meta {
  font-size: 0.9rem;
  color: #888;
}
</style>
