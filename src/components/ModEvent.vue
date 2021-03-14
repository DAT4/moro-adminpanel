<template>
    <div class="mt-4">
        <h1>Modify Event</h1>
        hej
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ModEvent',
  data() {
      return {
          response: '',
          event: {
              title: '',
              time: '',
              price: '',
              location: {
                  name: '',
                  citypart: '',
                  address: {
                      street: '',
                      no: '',
                  },
                  coordinates: {
                      longitude: '',
                      latitude: '',
                  },
              },
          },
      }
  },
  methods: {
      async postEvent() {
          const res = await axios.post('http://localhost:8070/addEvent', this.event);
          this.reponse = res.data;
      },
  }
}
</script>

<style scoped>
</style>
