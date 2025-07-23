
<script setup lang="ts">
import EventCard from '@/components/EventCard.vue';
// import  EventCategory from '@/components/EventCategory.vue';
import type { Event } from '@/types';
import { ref, onMounted } from 'vue';
import EventService from '@/services/EventService';
// const events = ref<Event[]>([
//   {
//     id: 5928101,
//     category: 'animal welfare',
//     title: 'Cat Adoption Day',
//     description: 'Find your new feline friend at this event.',
//     location: 'Meow Town',
//     date: 'January 28, 2022',
//     time: '12:00',
//     petsAllowed: true,
//     organizer: 'Kat Laydee'
//   },
//   {
//     id: 4582797,
//     category: 'food',
//     title: 'Community Gardening',
//     description: 'Join us as we tend to the community edible plants.',
//     location: 'Flora City',
//     date: 'March 14, 2022',
//     time: '10:00',
//     petsAllowed: true,
//     organizer: 'Fern Pollin'
//   },
//   {
//     id: 8419988,
//     category: 'sustainability',
//     title: 'Beach Cleanup',
//     description: 'Help pick up trash along the shore.',
//     location: 'Playa Del Carmen',
//     date: 'July 22, 2022',
//     time: '11:00',
//     petsAllowed: false,
//     organizer: 'Carey Wales'
//   }
// ]);

const events = ref<Event[]>();

onMounted(() =>{
  EventService.getEvents()
    .then(response => {
      events.value = response.data;
    })
    .catch(error => {
      console.error('There was an error!', error);
    });
});

</script>

<template>
  <!-- new element -->
  <h1>Events For Good</h1>
  
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <!-- <EventCategory v-for="event in events" :key="event.id" :event="event" /> -->
  </div>
</template>


  <!-- /* .events-wrapper {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    align-items: center;
  }
  .event {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    width: 320px;
  } */ -->

   <style scoped>

.event-class {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .events-wrapper {
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

.event {
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

.event:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
}

.event h3 {
  margin: 0 0 0.5rem;
  font-size: 1.25rem;
  color: #1f2937;
}

.event p {
  margin: 0;
  color: #4b5563;
  font-size: 1rem;
  line-height: 1.5;
} */
</style>


