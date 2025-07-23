<script setup lang="ts">
import { ref } from 'vue';
import type { Event } from '@/types';
 defineProps<{
  event: Event;
}>();
// const event = ref({
//   id: '5928101',
//   category: 'animal Welfare',
//   title: 'Cat Adoption Day',
//   description: 'Find your new feline friend at this event. ',
//   date: 'January 28, 2022',
//   time: '12:00',
//   petsAllowed: true,
//   organizer: 'Kat Laydee'
// });

</script>

<template>
  
  <div class="event-class">
    <div class="event-card">
      <h2>{{ event.title }}</h2>
      <span>@{{ event.time }} on {{ event.date }}</span> <br>
      <span> Category :{{ event.category }} </span><br>
      <span> Organizer :{{ event.organizer }} </span>
    </div>
  </div>

</template>

<style scoped>
.event-card {
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.06);
  padding: 20px;
  margin-bottom: 20px;
  width: 320px;
  text-align: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  font-family: 'Segoe UI', sans-serif;
}

.event-card:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12); 
  border-color: #94a3b8; 
}


.event-card h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
  color: #111827;
}

.event-card p {
  margin: 0;
  font-size: 0.95rem;
  color: #4b5563;
  line-height: 1.5;
}

</style>