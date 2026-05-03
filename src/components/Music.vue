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
  { id: 1, title: 'Alaskarma', role: 'Experimental', soundcloudId: 'SOUNDCLOUD_ID_1', year: 2025 },
  { id: 2, title: 'No One', role: 'Single', soundcloudId: 'SOUNDCLOUD_ID_2', year: 2025 },
  { id: 3, title: 'Passive Aggressive', role: 'Alternative', soundcloudId: 'SOUNDCLOUD_ID_3', year: 2024 },
  { id: 4, title: 'Suoneria Bastardi', role: 'Interlude', soundcloudId: 'SOUNDCLOUD_ID_4', year: 2025 },
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

.soundcloud-embed {
  width: 100%;
  margin: 1rem 0;
  border-radius: 5px;
  overflow: hidden;
}

.soundcloud-embed iframe {
  border: none;
}

.meta {
  font-size: 0.9rem;
  color: #888;
}
</style>
