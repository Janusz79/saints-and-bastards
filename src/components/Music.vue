<template>
  <section class="music">
    <h2>La Nostra Musica</h2>
    <div class="tracks">
      <div v-for="track in tracks" :key="track.id" class="track-card">
        <div class="track-header">
          <h3>{{ track.title }}</h3>
          <p class="role">{{ track.role }}</p>
        </div>
        <div class="player-container">
          <iframe 
            width="100%" 
            height="120" 
            scrolling="no" 
            frameborder="no" 
            allow="autoplay" 
            :src="`https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/${track.soundcloudId}&color=%23ff6b6b&auto_play=false&hide_related=true&hide_comments=true&show_user=false&show_reposts=false&show_teaser=false`">
          </iframe>
        </div>
        <a :href="`https://soundcloud.com/search?q=${encodeURIComponent(track.title)}`" target="_blank" rel="noopener noreferrer" class="soundcloud-link">
          <span>Ascolta su SoundCloud</span>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M10 5v14M4 9v6M16 3v18M22 8v8"></path>
          </svg>
        </a>
        <p class="meta">{{ track.year }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const tracks = ref([
  { id: 1, title: 'Alaskarma Live', role: 'Live', soundcloudId: '2313943499', year: 2026 },
  { id: 2, title: 'No One Else But Me', role: 'Sala Prove', soundcloudId: '2313944753', year: 2026 },
  { id: 3, title: 'Passive Aggressive', role: 'Sala Prove', soundcloudId: '2313944990', year: 2026 },
])
</script>
<style scoped>
.music {
  padding: 3rem 2rem;
  margin-top: 120px;
  max-width: 1400px;
  margin-left: auto;
  margin-right: auto;
}

.music h2 {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  color: #ff6b6b;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-weight: 700;
}

.tracks {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2.5rem;
}

.track-card {
  background: rgba(255, 255, 255, 0.05);
  padding: 1.5rem;
  border: 2px solid rgba(255, 107, 107, 0.4);
  border-radius: 8px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.track-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.05), rgba(255, 82, 82, 0.02));
  pointer-events: none;
}

.track-card:hover {
  transform: translateY(-8px);
  border-color: #ff6b6b;
  background: rgba(255, 107, 107, 0.08);
  box-shadow: 0 10px 30px rgba(255, 107, 107, 0.15);
}

.track-card h3 {
  color: #ff6b6b;
  margin: 0 0 0.3rem 0;
  font-size: 1.1rem;
  font-weight: 600;
  position: relative;
  z-index: 1;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.track-header {
  margin-bottom: 1rem;
}

.player-container {
  width: 100%;
  margin: 1rem 0;
  border-radius: 6px;
  overflow: hidden;
  position: relative;
  z-index: 1;
  border: 1px solid rgba(255, 107, 107, 0.2);
}

.player-container iframe {
  border: none;
  display: block;
  background: rgba(0, 0, 0, 0.5);
}

.soundcloud-link {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.8rem 1rem;
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.15), rgba(255, 82, 82, 0.08));
  border: 1px solid rgba(255, 107, 107, 0.3);
  border-radius: 4px;
  color: #ff6b6b;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 600;
  transition: all 0.3s ease;
  position: relative;
  z-index: 1;
  margin: 0.5rem 0;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.soundcloud-link:hover {
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.25), rgba(255, 82, 82, 0.15));
  border-color: #ff6b6b;
  transform: translateX(4px);
}

.soundcloud-link svg {
  width: 16px;
  height: 16px;
  stroke: #ff6b6b;
}

.role {
  color: #ff6b6b !important;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 0.75rem;
  letter-spacing: 1.5px;
  margin: 0 !important;
  position: relative;
  z-index: 1;
}

.track-card p {
  color: #aaa;
  margin: 0;
  position: relative;
  z-index: 1;
}

.meta {
  font-size: 0.9rem;
  color: #888;
  position: relative;
  z-index: 1;
  font-weight: 600;
}
</style>
