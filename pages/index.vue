<template>
  <div class="container">
    <div>
      <h1 class="title">
        Events
      </h1>
      <EventCard
        v-for="(event, index) in events"
        :key="index"
        :event="event"
        :data-index="index"
      />
    </div>
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import {mapState} from 'vuex'

export default {

  head(){
    return {
      title: 'Event-Listening',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'where you can find what you need'
        }
      ]
    }
  },
  components: {
    EventCard
  },
  // asyncData({$axios , error}){
  //   return $axios.get('http://localhost:3000/events')
  //   .then(response => {
  //     return {
  //       events: response.data
  //     }
  //   })
  //   .catch(e => {
  //     error({
  //       statusCode: 503,
  //       message:'Unable to fetch events at this time'
  //     })
  //   })
  // },
  async  fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')

    }
    catch(e) {
      error({
        statusCode: 503,
        message:'Unable to fetch events at this time'
      })
    }
  },
  computed: mapState({
    events: state => state.events.events
  })
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
