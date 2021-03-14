<template>
  <div class="row mt-4">
    <h1>Events</h1>
    <input
      v-on:click="getEvents"
      class="btn btn-dark btn-sm"
      value="load events"
    />

    <div class="m-2 list-group">
      <a
        class="list-group-item-action list-group-item"
        v-for="event in events"
        :key="event.Title"
        :class="event.class.chosen ? 'active' : ''"
        v-on:click="setCurrent(event)"
      >
        {{ event.Title }}
      </a>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "EventList",
  data() {
    return {
      current: null,
      events: [],
    };
  },
  methods: {
    setCurrent(item) {
      this.current.class.chosen = false;
      this.current = item;
      this.current.class.chosen = true;
    },
    async getEvents() {
      var token = `bearer ${window.localStorage.getItem("moroToken")}`;
      console.log(token);
      const res = await axios.get("http://localhost:8070/startScrape", {
        params: { place: "huset" },
        headers: {
          Authorization: token,
        },
      });
      this.events = res.data;
      this.events.forEach((event) => {
        event.class = {
          chosen: false,
        };
      });
    },
  },
};
</script>

<style scoped></style>
