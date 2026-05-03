<template>
  <section class="tour">
    <h2>Prossime Date</h2>
    <div class="tour-list">
      <div v-for="date in tourDates" :key="date.id" class="tour-date">
        <div class="date">{{ formatDate(date.date) }}</div>
        <div class="venue">
          <h3>{{ date.venue }}</h3>
          <p>{{ date.city }}</p>
        </div>
        <button class="tickets-btn">Biglietti</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const tourDates = ref([
  { id: 1, date: '2026-06-15', venue: 'Stadio San Paolo', city: 'Napoli' },
  { id: 2, date: '2026-07-22', venue: 'Arena di Verona', city: 'Verona' },
  { id: 3, date: '2026-08-10', venue: 'Palasport Olimpico', city: 'Roma' },
])

const formatDate = (date) => {
  const d = new Date(date)
  return d.toLocaleDateString('it-IT', { day: '2-digit', month: 'long', year: 'numeric' })
}
</script>

<style scoped>
.tour {
  padding: 2rem 0;
}

.tour h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: #ff6b6b;
  text-transform: uppercase;
}

.tour-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.tour-date {
  display: flex;
  align-items: center;
  gap: 2rem;
  background: rgba(255, 255, 255, 0.05);
  padding: 1.5rem;
  border-left: 5px solid #ff6b6b;
  transition: background 0.3s;
}

.tour-date:hover {
  background: rgba(255, 107, 107, 0.1);
}

.date {
  font-size: 1.1rem;
  font-weight: bold;
  color: #ff6b6b;
  min-width: 120px;
}

.venue h3 {
  color: #fff;
  margin-bottom: 0.3rem;
}

.venue p {
  color: #aaa;
  font-size: 0.9rem;
}

.tickets-btn {
  margin-left: auto;
  padding: 0.7rem 1.5rem;
  background: #ff6b6b;
  color: #fff;
  border: none;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

.tickets-btn:hover {
  background: #ff5252;
}
</style>
