<template>
  <div class="mx-auto">
    <div class="m-2 row">
      <Login />
      <ModEvent />
      <EventList />
    </div>
  </div>
</template>

<script>
import Login from "./components/Login.vue";
import EventList from "./components/EventList.vue";
import ModEvent from "./components/ModEvent.vue";

export default {
  name: "App",
  components: {
    Login,
    EventList,
    ModEvent,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Anton");
h1 {
  font-family: "Anton", sans-serif;
}
</style>
