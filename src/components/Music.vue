<template>
  <section class="music">
    <h2>La Nostra Musica</h2>
    <div class="tracks">
      <div v-for="track in tracks" :key="track.id" class="track-card">
        <h3>{{ track.title }}</h3>
        <p class="role">{{ track.role }}</p>
        <div class="soundcloud-embed">
          <iframe 
            width="100%" 
            height="166" 
            scrolling="no" 
            frameborder="no" 
            allow="autoplay" 
            :src="`https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/${track.soundcloudId}&color=%23ff6b6b&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true`">
          </iframe>
        </div>
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
  margin: 0 0 0.5rem 0;
  font-size: 1.2rem;
  font-weight: 600;
  position: relative;
  z-index: 1;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.track-card p {
  color: #aaa;
  margin: 0.5rem 0;
  position: relative;
  z-index: 1;
}

.role {
  color: #ff6b6b !important;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 0.8rem;
  letter-spacing: 1.5px;
  margin-bottom: 1rem !important;
}

.soundcloud-embed {
  width: 100%;
  margin: 1.5rem 0;
  border-radius: 6px;
  overflow: hidden;
  position: relative;
  z-index: 1;
  border: 1px solid rgba(255, 107, 107, 0.2);
}

.soundcloud-embed iframe {
  border: none;
  display: block;
}

.meta {
  font-size: 0.9rem;
  color: #888;
  position: relative;
  z-index: 1;
  font-weight: 600;
}
</style>
