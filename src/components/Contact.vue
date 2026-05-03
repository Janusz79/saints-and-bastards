<template>
  <section class="contact">
    <h2>Contattaci</h2>
    <div class="contact-content">
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="name">Nome</label>
          <input v-model="form.name" type="text" id="name" required>
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input v-model="form.email" type="email" id="email" required>
        </div>
        <div class="form-group">
          <label for="message">Messaggio</label>
          <textarea v-model="form.message" id="message" rows="5" required></textarea>
        </div>
        <button type="submit" class="submit-btn">Invia</button>
      </form>
      <div class="contact-info">
        <h3>Info</h3>
        <p><strong>Email:</strong> info@saintsandbastards.com</p>
        <p><strong>Telefono:</strong> +39 123 456 7890</p>
        <p><strong>Città:</strong> Viareggio</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  alert('Grazie per il messaggio! Ti risponderemo presto.')
  form.value = { name: '', email: '', message: '' }
}
</script>

<style scoped>
.contact {
  padding: 2rem 0;
  margin-top: 120px;
}

.contact h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: #ff6b6b;
  text-transform: uppercase;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  margin-bottom: 0.5rem;
  font-weight: bold;
  color: #ff6b6b;
}

.form-group input,
.form-group textarea {
  padding: 0.75rem;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid #ff6b6b;
  color: #fff;
  font-family: inherit;
  font-size: 0.95rem;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  background: rgba(255, 107, 107, 0.1);
  border-color: #fff;
}

.submit-btn {
  padding: 0.75rem;
  background: #ff6b6b;
  color: #fff;
  border: none;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
  text-transform: uppercase;
}

.submit-btn:hover {
  background: #ff5252;
}

.contact-info h3 {
  color: #ff6b6b;
  margin-bottom: 1rem;
}

.contact-info p {
  margin-bottom: 0.75rem;
  color: #ccc;
}

@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
  }
}
</style>
