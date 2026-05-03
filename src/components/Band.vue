<template>
  <section class="band">
    <h2>LA BAND</h2>
    
    <!-- First row: 3 members -->
    <div class="band-members">
      <div class="member">
        <div class="member-avatar">CBA</div>
        <h3>Christian Bernard Allison</h3>
        <p class="role">Voce</p>
        <p class="bio">Frontman della band dal 2025, con una voce che fa vibrare le folle.</p>
      </div>
      <div class="member">
        <div class="member-avatar">EP</div>
        <h3>Enrico Pardini</h3>
        <p class="role">Chitarra e Synth</p>
        <p class="bio">Chitarrista e tastierista della band, con un talento per i riff coinvolgenti.</p>
      </div>
      <div class="member">
        <div class="member-avatar">RL</div>
        <h3>Riccardo Lari</h3>
        <p class="role">Chitarra</p>
        <p class="bio">Chitarrista solista della band, con un talento per i assoli coinvolgenti.</p>
      </div>
    </div>

    <!-- Second row: 2 members centered -->
    <div class="band-members-bottom">
      <div class="member">
        <div class="member-avatar">DAS</div>
        <h3>Davide Alessandro Simoncini</h3>
        <p class="role">Basso</p>
        <p class="bio">Il groove maker, il cuore ritmico della band.</p>
      </div>
      <div class="member">
        <div class="member-avatar">TG</div>
        <h3>Tommaso Giorgi</h3>
        <p class="role">Batteria</p>
        <p class="bio">Batterista esplosivo, regista della potenza del suono.</p>
      </div>
    </div>
  </section>
</template>

<script setup>
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
  padding: 2rem;
  border: 1px solid rgba(255, 107, 107, 0.2);
  border-radius: 10px;
  text-align: center;
  transition: all 0.3s;
}

.member:hover {
  background: rgba(255, 107, 107, 0.1);
  border-color: #ff6b6b;
  transform: translateY(-10px);
}

.member-avatar {
  width: 100px;
  height: 100px;
  margin: 0 auto 1.5rem;
  background: linear-gradient(135deg, #ff6b6b, #ff5252);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: bold;
  color: #fff;
}

.member h3 {
  color: #fff;
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.member .role {
  color: #ff6b6b;
  font-weight: 600;
  margin-bottom: 1rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.9rem;
}

.member .bio {
  color: #aaa;
  font-size: 0.95rem;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .band h2 {
    font-size: 1.8rem;
  }

  .band-members {
    grid-template-columns: 1fr;
  }
}
</style>
