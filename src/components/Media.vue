<template>
  <section class="media">
    <h2>Media</h2>
    <div class="media-grid">
      <div class="media-item">
        <a href="https://www.youtube.com/watch?v=ALASKARMA_ID" target="_blank" rel="noopener noreferrer">
          <img src="/images/Alaskarma.png" alt="Alaskarma" class="video-thumbnail" />
          <div class="play-overlay">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M8 5v14l11-7z"/>
            </svg>
          </div>
          <h3>Alaskarma</h3>
          <p class="video-source">Watch on YouTube</p>
        </a>
      </div>
      <div class="media-item">
        <a href="https://www.youtube.com/watch?v=NOONE_LIVE_ID" target="_blank" rel="noopener noreferrer">
          <img src="/images/No one Live @PoolJazz.png" alt="No one Live @PoolJazz" class="video-thumbnail" />
          <div class="play-overlay">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M8 5v14l11-7z"/>
            </svg>
          </div>
          <h3>No one Live @PoolJazz</h3>
          <p class="video-source">Watch on YouTube</p>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
// Videos are now hosted on YouTube - links in template
</script>

<style scoped>
.media {
  padding: 2rem 0;
  margin-top: 120px;
}

.media h2 {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  color: #ff6b6b;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-align: center;
}

.media-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.media-item {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 107, 107, 0.2);
  border-radius: 10px;
  overflow: hidden;
  transition: all 0.3s;
}

.media-item a {
  display: block;
  text-decoration: none;
  color: inherit;
  cursor: pointer;
}

.media-item:hover {
  border-color: #ff6b6b;
  transform: translateY(-10px);
  background: rgba(255, 107, 107, 0.1);
}

.media-item:hover .play-overlay {
  background: rgba(255, 107, 107, 0.3);
}

.video-thumbnail {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  display: block;
}

.play-overlay {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 60px;
  height: 60px;
  background: rgba(255, 107, 107, 0.8);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  transition: all 0.3s;
}

.play-overlay svg {
  width: 30px;
  height: 30px;
}

.media-item h3 {
  color: #fff;
  padding: 1.5rem 1.5rem 0.5rem;
  margin: 0;
  font-size: 1.1rem;
}

.video-source {
  color: #ff6b6b;
  padding: 0 1.5rem 1.5rem;
  margin: 0;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .media h2 {
    font-size: 1.8rem;
  }

  .media-grid {
    grid-template-columns: repeat(1, 1fr);
    padding: 1rem;
  }
}
</style>
