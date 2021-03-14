<template>
  <div class="row mt-4">
    <h1>Login</h1>
    <p>Please enter your login and password!</p>
    <input
      class="border border-dark mt-2"
      type="text"
      v-model="user.username"
    />
    <input
      class="border border-dark mt-2"
      type="password"
      v-model="user.password"
    />
    <input
      class="btn btn-outline-dark mt-2 btn-sm"
      value="Login"
      v-on:click="login"
    />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      user: {
        username: "",
        password: "",
        authenticated: false,
      },
      token: "",
    };
  },
  props: {
    msg: String,
  },
  methods: {
    async login() {
      const res = await axios.post("http://localhost:8070/login", this.user);
      this.user.authenticated = true;
      this.token = res.data.token;
      window.localStorage["moroToken"] = res.data.token;
    },
  },
};
</script>

<style scoped></style>
