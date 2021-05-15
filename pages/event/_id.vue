<template>
    <div>
        <h1>{{event.title}}</h1>
        <p>{{event.name}}</p>
    </div>
</template>



<script>
import {mapState} from 'vuex'

export default {
    head(){
        return {
            title:  this.event.title,
        }
    },
      async  fetch({ store, error, params }) {
    try {
       await store.dispatch( 'events/fetchEvent' ,params.id)

    }
    catch(e) {
      error({
        statusCode: 503,
        message:'Unable to fetch events at this time#' + params.id
      })
    }
  },
  computed: mapState ({
    event:state => state.events.event
  })
}
</script>

<style>

</style>