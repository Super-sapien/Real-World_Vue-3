<template>
  <div v-if="event" class="event-details">
    <span>@{{ event.time }} on {{ event.date }}</span>
    <h4>{{ event.title }}</h4>
    <h5>{{ event.location }}</h5>
    <h6>{{ event.description }}</h6>
    <p>{{ event.organizer }}</p>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'

export default {
  props: ['id'],
  data() {
    return {
      event: null
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then(response => {
        this.event = response.data
      })
      .catch(error => {
        console.log(error)
      })
  }
}
</script>

<style scoped>
/* .event-details {
  padding: 20px;
  width: 250px;
  border: 1px solid #39495c;
  margin-bottom: 18px;
} */
</style>
