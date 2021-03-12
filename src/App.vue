<template>
  <div class="container">
    <div class="row">
        <Login/>
    </div>
  </div>
</template>

<script>
import Login from './components/Login.vue'

export default {
  name: 'App',
  components: {
    Login
  }
}
</script>

<style>
#app {
  padding-top: 100px;
  padding-bottom: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #6200ee;
  background: linear-gradient(to right, #CE93D8, #CCFFC8);
}
</style>
