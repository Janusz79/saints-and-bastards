<template>
  <section class="band">
    <h2>LA BAND</h2>
    
    <!-- First row: 3 members -->
    <div class="band-members">
      <div class="member">
        <div class="member-image">
          <img src="/images/christian.webp" alt="Christian Bernard Allison" @error="handleImageError" />
        </div>
        <h3>Christian Bernard Allison</h3>
        <p class="role">Voce</p>
        <p class="bio">Frontman della band dal 2025, con una voce che fa vibrare le folle.</p>
      </div>
      <div class="member">
        <div class="member-image">
          <img src="/images/enrico.webp" alt="Enrico Pardini" @error="handleImageError" />
        </div>
        <h3>Enrico Pardini</h3>
        <p class="role">Chitarra e Synth</p>
        <p class="bio">Chitarrista e tastierista della band, con un talento per i riff coinvolgenti.</p>
      </div>
      <div class="member">
        <div class="member-image">
          <img src="/images/riccardo.webp" alt="Riccardo Lari" @error="handleImageError" />
        </div>
        <h3>Riccardo Lari</h3>
        <p class="role">Chitarra</p>
        <p class="bio">Chitarrista solista della band, con un talento per i assoli coinvolgenti.</p>
      </div>
    </div>

    <!-- Second row: 2 members centered -->
    <div class="band-members-bottom">
      <div class="member">
        <div class="member-image">
          <img src="/images/davide.webp" alt="Davide Alessandro Simoncini" @error="handleImageError" />
        </div>
        <h3>Davide Alessandro Simoncini</h3>
        <p class="role">Basso</p>
        <p class="bio">Il groove maker, il cuore ritmico della band.</p>
      </div>
      <div class="member">
        <div class="member-image">
          <img src="/images/tommaso.webp" alt="Tommaso Giorgi" @error="handleImageError" />
        </div>
        <h3>Tommaso Giorgi</h3>
        <p class="role">Batteria</p>
        <p class="bio">Batterista esplosivo, regista della potenza del suono.</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const handleImageError = (e) => {
  e.target.classList.add('image-error')
}
</script>

<style scoped>
.band {
  padding: 2rem 0;
  margin-top: 120px;
}

.band h2 {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  color: #ff6b6b;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-align: center;
}

.band-members {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.band-members-bottom {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
  max-width: 700px;
  margin: 2rem auto 0;
}

.member:nth-child(4) {
  grid-column: 2;
}

.member:nth-child(5) {
  grid-column: 3;
}

.member {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 107, 107, 0.2);
  border-radius: 10px;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
  height: 500px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.member:hover {
  border-color: #ff6b6b;
  transform: translateY(-10px);
}

.member-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  margin-bottom: 0;
  border-radius: 0;
  overflow: hidden;
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(255, 82, 82, 0.1));
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 0;
}

.member-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
}

.member-image img.image-error {
  display: none;
}

.member h3 {
  color: #fff;
  margin: 0;
  font-size: 1.3rem;
  position: relative;
  z-index: 2;
  padding: 0 1.5rem;
}

.member .role {
  color: #ff6b6b;
  font-weight: 600;
  margin: 0.5rem 0 1rem 0;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.9rem;
  position: relative;
  z-index: 2;
  padding: 0 1.5rem;
}

.member .bio {
  color: #aaa;
  font-size: 0.95rem;
  line-height: 1.6;
  position: relative;
  z-index: 2;
  padding: 0 1.5rem 1.5rem 1.5rem;
  margin: 0;
}

/* Gradient overlay dal basso */
.member::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 60%;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.5) 50%, transparent);
  z-index: 1;
  border-radius: 10px;
}

@media (max-width: 768px) {
  .band h2 {
    font-size: 1.8rem;
  }

  .band-members {
    grid-template-columns: 1fr;
  }

  .member {
    height: 400px;
  }
}
</style>
