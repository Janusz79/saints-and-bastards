<template>
  <section class="live">
    <h2>Prossimi Concerti</h2>
    <div class="tour-list">
      <div v-for="date in tourDates" :key="date.id" class="tour-date">
        <div class="date-box">
          <div class="day">{{ formatDay(date.date) }}</div>
          <div class="month">{{ formatMonth(date.date) }}</div>
        </div>
        <div class="venue-info">
          <h3>{{ date.venue }}</h3>
          <p>{{ date.city }}</p>
          <p class="time">{{ date.time }}</p>
        </div>
        <button class="tickets-btn">Biglietti</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const tourDates = ref([
  { id: 1, date: '2026-06-15', time: '21:00', venue: 'Stadio San Paolo', city: 'Napoli' },
  { id: 2, date: '2026-07-22', time: '20:30', venue: 'Arena di Verona', city: 'Verona' },
  { id: 3, date: '2026-08-10', time: '21:30', venue: 'Palasport Olimpico', city: 'Roma' },
  { id: 4, date: '2026-09-05', time: '20:00', venue: 'Palalido', city: 'Milano' },
])

const formatDay = (date) => {
  return new Date(date).toLocaleDateString('it-IT', { day: '2-digit' })
}

const formatMonth = (date) => {
  return new Date(date).toLocaleDateString('it-IT', { month: 'short' }).toUpperCase()
}
</script>

<style scoped>
.live {
  padding: 2rem 0;
}

.live h2 {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  color: #ff6b6b;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-align: center;
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
  border-left: 4px solid #ff6b6b;
  transition: all 0.3s;
}

.tour-date:hover {
  background: rgba(255, 107, 107, 0.1);
  transform: translateX(10px);
}

.date-box {
  background: linear-gradient(135deg, #ff6b6b, #ff5252);
  padding: 1.5rem;
  border-radius: 8px;
  text-align: center;
  min-width: 100px;
}

.date-box .day {
  font-size: 2rem;
  font-weight: bold;
  color: #fff;
}

.date-box .month {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.8);
  letter-spacing: 1px;
}

.venue-info {
  flex: 1;
}

.venue-info h3 {
  color: #fff;
  margin: 0 0 0.5rem 0;
  font-size: 1.2rem;
}

.venue-info p {
  color: #aaa;
  margin: 0.3rem 0;
  font-size: 0.95rem;
}

.venue-info .time {
  color: #ff6b6b;
  font-weight: 600;
}

.tickets-btn {
  padding: 0.8rem 1.8rem;
  background: #ff6b6b;
  color: #fff;
  border: none;
  cursor: pointer;
  font-weight: bold;
  transition: all 0.3s;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.85rem;
}

.tickets-btn:hover {
  background: #ff5252;
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .live h2 {
    font-size: 1.8rem;
  }

  .tour-date {
    flex-wrap: wrap;
    gap: 1rem;
  }

  .tickets-btn {
    width: 100%;
  }
}
</style>
