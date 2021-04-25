<template>
    <div v-if="event">
        <h1>{{ event.title }}</h1>
        <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
        <p>{{ event.description }}</p>
    </div>
</template>


<script>
import EventService from '@/services/EventService.js'

export default {

    props: ['id'],

    data() {
        return {
            event: null
           //id: 123
            // in this case we wqant a single event
        }
    },

// fetch even (by id) and set local date
    created() {
        EventService.getEvent(this.id)
        .then((response) => {
            console.log('event:', response.data)
            this.event = response.data
        }) 
        .catch((error) => {
            console.log(error)
        })
    },


}

</script>