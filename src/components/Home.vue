<template>
  <section class="home">
    <div class="hero">
      <h2>Saints & Bastards</h2>
      <p>La miglior band rock della scena</p>
      <button class="cta-btn">Ascolta Ora</button>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.home {
  padding: 4rem 2rem;
}

.hero {
  text-align: center;
  padding: 3rem 0;
  animation: fadeIn 1s ease-in;
}

.hero h2 {
  font-size: 3rem;
  margin-bottom: 1rem;
  color: #ff6b6b;
  text-transform: uppercase;
}

.hero p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  color: #ccc;
}

.cta-btn {
  padding: 1rem 2rem;
  background: #ff6b6b;
  color: #fff;
  border: none;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
  text-transform: uppercase;
}

.cta-btn:hover {
  background: #ff5252;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
