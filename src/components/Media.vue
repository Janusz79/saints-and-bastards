<template>
  <section class="media">
    <h2>Media</h2>
    <div class="media-grid">
      <div class="media-item video-player">
        <video width="100%" height="100%" controls poster="/images/Alaskarma.png">
          <source src="/video/Alaskarma.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <h3>Alaskarma</h3>
      </div>
      <div class="media-item video-player">
        <video width="100%" height="100%" controls poster="/images/No one Live @PoolJazz.png">
          <source src="/video/No one Live @PoolJazz.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <h3>No one Live @PoolJazz</h3>
      </div>
    </div>
  </section>
</template>

<script setup>
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
  cursor: pointer;
}

.media-item:hover {
  border-color: #ff6b6b;
  transform: translateY(-10px);
  background: rgba(255, 107, 107, 0.1);
}

.media-thumb {
  width: 100%;
  aspect-ratio: 1;
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(255, 82, 82, 0.1));
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  color: #ff6b6b;
}

.media-thumb svg {
  width: 80px;
  height: 80px;
}

.media-item h3 {
  color: #fff;
  padding: 1.5rem 1.5rem 0.5rem;
  margin: 0;
  font-size: 1.1rem;
}

.media-item p {
  color: #aaa;
  padding: 0 1.5rem 1.5rem;
  margin: 0;
  font-size: 0.9rem;
}

.media-item.video .media-thumb {
  background: rgba(255, 0, 0, 0.1);
}

.media-item.video-player {
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.media-item.video-player video {
  width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}

.media-item.video-player h3 {
  padding: 1rem 1.5rem 0.5rem;
}

.media-item.video .media-thumb {
  color: #ff0000;
}

.media-item.gallery .media-thumb {
  background: rgba(0, 150, 255, 0.1);
}

.media-item.gallery .media-thumb {
  color: #0096ff;
}

.media-item.album .media-thumb {
  background: rgba(100, 200, 255, 0.1);
}

.media-item.album .media-thumb {
  color: #64c8ff;
}

.media-item.podcast .media-thumb {
  background: rgba(200, 100, 255, 0.1);
}

.media-item.podcast .media-thumb {
  color: #c864ff;
}

@media (max-width: 768px) {
  .media h2 {
    font-size: 1.8rem;
  }

  .media-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .media-thumb svg {
    width: 60px;
    height: 60px;
  }
}
</style>
