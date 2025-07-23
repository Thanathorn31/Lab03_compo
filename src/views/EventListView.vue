
<script setup lang="ts">
import EventCard from '@/components/EventCard.vue';
// import  EventCategory from '@/components/EventCategory.vue';
import type { Event } from '@/types';
import { ref, onMounted ,computed} from 'vue';
import EventService from '@/services/EventService';

const events = ref<Event[]>();

const props = defineProps({
  page: {
    type: Number,
    required: true
  }
})
const page = computed(() => props.page);

onMounted(() =>{
  EventService.getEvents(2, page.value)
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




   <style scoped>

/* .evens{
  display: flex;
  justify-content: center;
  align-items: center;
} */

</style>


