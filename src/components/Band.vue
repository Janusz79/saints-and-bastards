<template>
  <section class="band">
    <h2>LA BAND</h2>
    <div class="band-members">
      <div class="member">
        <div class="member-avatar">JS</div>
        <h3>John Smith</h3>
        <p class="role">Voce</p>
        <p class="bio">Frontman della band dal 2015, con una voce che fa vibrare le folle.</p>
      </div>
      <div class="member">
        <div class="member-avatar">MD</div>
        <h3>Marco Del Rio</h3>
        <p class="role">Chitarra</p>
        <p class="bio">Chitarrista virtuoso, autore di tutti i riff più esplosivi.</p>
      </div>
      <div class="member">
        <div class="member-avatar">LC</div>
        <h3>Luca Conti</h3>
        <p class="role">Basso</p>
        <p class="bio">Il groove maker, il cuore ritmico della band.</p>
      </div>
      <div class="member">
        <div class="member-avatar">AF</div>
        <h3>Andrea Falcon</h3>
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
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
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
