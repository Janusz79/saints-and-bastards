<template>
  <section class="media">
    <h2>Media</h2>
    <div class="media-grid">
      <div class="media-item video-player" @click="openVideo('Alaskarma', '/video/Alaskarma.mp4')">
        <img src="/images/Alaskarma.png" alt="Alaskarma" class="video-thumbnail" />
        <div class="play-overlay">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M8 5v14l11-7z"/>
          </svg>
        </div>
        <h3>Alaskarma</h3>
      </div>
      <div class="media-item video-player" @click="openVideo('No one Live @PoolJazz', '/video/No one Live @PoolJazz.mp4')">
        <img src="/images/No one Live @PoolJazz.png" alt="No one Live @PoolJazz" class="video-thumbnail" />
        <div class="play-overlay">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M8 5v14l11-7z"/>
          </svg>
        </div>
        <h3>No one Live @PoolJazz</h3>
      </div>
    </div>

    <!-- Video Modal -->
    <Transition name="modal-fade">
      <div v-if="showModal" class="video-modal" @click.self="closeVideo">
        <div class="modal-content">
          <button class="close-btn" @click="closeVideo">✕</button>
          <video controls autoplay preload="metadata">
            <source :src="selectedVideoSrc" type="video/mp4">
            Your browser does not support the video tag.
          </video>
        </div>
      </div>
    </Transition>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const showModal = ref(false)
const selectedVideoTitle = ref('')
const selectedVideoSrc = ref('')

const openVideo = (title, src) => {
  selectedVideoTitle.value = title
  selectedVideoSrc.value = src
  showModal.value = true
}

const closeVideo = () => {
  showModal.value = false
}
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
  position: relative;
}

.video-thumbnail {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  display: block;
}

.play-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.3);
  transition: background 0.3s;
}

.media-item.video-player:hover .play-overlay {
  background: rgba(0, 0, 0, 0.5);
}

.play-overlay svg {
  width: 60px;
  height: 60px;
  color: #ff6b6b;
}

.media-item.video-player h3 {
  padding: 1rem 1.5rem 0.5rem;
}

/* Video Modal */
.video-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.65);
  backdrop-filter: blur(5px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 2rem;
}

.modal-content {
  position: relative;
  width: 100%;
  max-width: 900px;
  aspect-ratio: 16 / 9;
}

.close-btn {
  position: absolute;
  top: -40px;
  right: 0;
  background: none;
  border: none;
  color: #fff;
  font-size: 2rem;
  cursor: pointer;
  z-index: 1001;
  transition: color 0.3s;
}

.close-btn:hover {
  color: #ff6b6b;
}

.modal-content video {
  width: 100%;
  height: 100%;
}

/* Modal Transition */
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.3s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

.modal-fade-enter-active .modal-content {
  animation: modal-slide-in 0.3s ease;
}

.modal-fade-leave-active .modal-content {
  animation: modal-slide-out 0.3s ease;
}

@keyframes modal-slide-in {
  from {
    transform: scale(0.9) translateY(-20px);
    opacity: 0;
  }
  to {
    transform: scale(1) translateY(0);
    opacity: 1;
  }
}

@keyframes modal-slide-out {
  from {
    transform: scale(1) translateY(0);
    opacity: 1;
  }
  to {
    transform: scale(0.9) translateY(-20px);
    opacity: 0;
  }
}


@media (max-width: 768px) {
  .media h2 {
    font-size: 1.8rem;
  }

  .media-grid {
    grid-template-columns: repeat(1, 1fr);
    padding: 1rem;

  }

  .media-thumb svg {
    width: 60px;
    height: 60px;
  }
}
</style>
